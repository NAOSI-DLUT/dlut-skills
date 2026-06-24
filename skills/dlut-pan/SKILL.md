---
name: dlut-pan
description: 大工云盘（pan.dlut.edu.cn）API 调用 skill。用于通过 sign_in 接口获取 token，并调用 list_folder、file download 等 API 列出目录和下载文件。适用于用户已持有大工账号且希望通过 API 直接操作云盘的场景。
---

# DLUT Pan API

## 目标

通过大工云盘公开 API 完成：
1. 使用账号密码获取访问 token。
2. 列出指定目录下的文件/文件夹。
3. 搜索文件名、全文内容或群组。
4. 下载文件。

## 前置条件

- 用户持有有效的大工统一身份认证账号和密码。
- 用户明确授权 agent 使用其账号信息调用 API。
- agent 不得在日志、文件或对话中保存账号密码或 token。

## 已知空间

| 空间 | root_id | 说明 |
|------|---------|------|
| NAOSI 资料云盘 | `ak7an4chdvtq` | 共享课程资料、上传及阅读指南等，是最大的公共资料云盘 |

> 个人空间 root_id 需通过登录后获取，与用户账号绑定。

**搜索/查资料时优先使用 NAOSI 的 `root_id`（`ak7an4chdvtq`）**，因为该组织公开且资料最丰富。若用户未加入该组织，则回退到个人空间。

## API 参考

详细接口定义见 `references/api-reference.md`。

## 工作流

### 1. 获取 token

优先尝试通过浏览器自动化获取 token，以减少用户手动向 agent 提供密码的环节。

#### 方式 A：Playwright 浏览器获取（优先）

如果当前 agent 支持 `open_browser_page` 等浏览器工具：

1. 打开浏览器页面：`http://pan.dlut.edu.cn/cas`
2. 提示用户在该页面完成统一身份认证（CAS）登录。若 CAS 需要验证码或二次认证，由用户手动处理。
3. 等待登录完成，页面通常会跳转回云盘主页（`http://pan.dlut.edu.cn/`）。
4. 使用 `run_playwright_code` 执行以下脚本提取 `token`。大工云盘将登录信息存储在 `localStorage.jStorage` 中，其结构为嵌套 JSON，需两层解析：

```javascript
return page.evaluate(() => {
  try {
    const jStorage = JSON.parse(localStorage.getItem('jStorage') || '{}');
    const data = JSON.parse(jStorage.data || '{}');
    return data.token || null;
  } catch {
    return null;
  }
});
```

5. 若上述方法未获取到 token（如云盘改版），可进一步尝试从 API 请求拦截、页面全局变量 `window.token` / `window.userInfo.token`，或刷新页面后检查网络请求中的 `token` 参数。
6. 获取 token 成功后，立即关闭浏览器页面。

#### 方式 B：API 直接登录（fallback）

若不支持浏览器工具，或浏览器方式未能获取 token，则使用 `POST` 请求直接调用登录接口。参数放在 query string 中，body 为空：

```
POST http://202.118.66.144:8088/v1/auth/sign_in
    ?link_device={device_name}
    &password={password}
    &link_name={link_name}
    &ldap_name={ldap_name}
    &username={username}

Content-Length: 0
```

参数说明：
- `username`: 学号/工号。
- `password`: 统一身份认证密码。
- `link_device`, `link_name`, `ldap_name`: 设备标识，可填入设备名或型号（如 `MEP-AN00`）。

返回体中包含 `token`，提取后用于后续请求。

### 2. 检查 NAOSI 组织成员资格（如适用）

在通过浏览器方式获取 token 时，可同时读取 `localStorage.jStorage` 中的用户组织信息：

```javascript
return page.evaluate(() => {
  try {
    const jStorage = JSON.parse(localStorage.getItem('jStorage') || '{}');
    const data = JSON.parse(jStorage.data || '{}');
    return data.groupIDs || null;
  } catch {
    return null;
  }
});
```

- 如果返回结果中包含键 `NAOSI`（或其 `rootID` 为 `ak7an4chdvtq`），说明用户已加入 NAOSI 资料云盘，后续搜索优先使用 `root_id=ak7an4chdvtq`。
- 如果用户未加入 NAOSI，agent 应**询问用户是否需要自动加入**。

#### 加入 NAOSI 组织

若用户同意加入，调用以下 API：

```
POST http://pan.dlut.edu.cn/v1/users/{user_id}/groups?group_id=ej7f8s176d8f&token={token}
Content-Type: application/json

{"remarks": ""}
```

参数说明：
- `user_id`: 从 `jStorage.data.userid` 获取。
- `group_id`: NAOSI 的组织 ID 为 `ej7f8s176d8f`（注意不是 `root_id`，而是 `groupID`）。
- `token`: 登录获取的 token。

返回示例：
```json
{
  "relation": {
    "is_activated": true,
    "role": { "name": "member", "display_value": "成员" }
  }
}
```

- 若 `relation.is_activated` 为 `true`，说明该群组为公开群，用户**直接加入成功**，后续即可使用 `root_id=ak7an4chdvtq` 操作。
- 若 `relation.is_activated` 为 `false`，说明需要群主审批，用户状态为"审批中"，agent 应提示用户等待审批通过后再操作。

如果用户拒绝加入或加入流程失败，后续操作回退到个人空间（使用用户自己的 `root_id`）。

### 3. 列出目录

```
POST http://pan.dlut.edu.cn/v1/fileops/list_folder
    ?root_id={root_id}
    &path={path}
    &token={token}
    &locale=zh_CN

Content-Length: 0
```

参数说明：
- `root_id`: 空间根目录 ID，优先使用 NAOSI 的 `ak7an4chdvtq`；若用户未加入则使用个人空间 `root_id`。
- `path`: 目录路径，根目录传 `%2F`（即 `/`）。
- `token`: 上一步获取的 token。

返回目录列表，字段通常包括：文件/目录名、类型、大小、更新时间、路径等。

### 4. 搜索

#### 搜索文件名

```
GET http://pan.dlut.edu.cn/v1/search/files
    ?query={keyword}
    &root_id={root_id}
    &token={token}
    [&path={path}]
    [&offset={offset}]
    [&limit={limit}]
```

参数说明：
- `query`: 搜索关键词。
- `root_id`: 空间根目录 ID（必填，否则返回 403）。**优先使用 `ak7an4chdvtq`（NAOSI）**；若用户未加入则使用个人空间 `root_id`。
- `token`: 登录获取的 token。
- `path`, `offset`, `limit`: 可选的范围和分页参数。

返回包含 `total`、`offset`、`entries` 的结果集，entries 为匹配文件/目录的元数据列表。

#### 搜索全文

```
GET http://pan.dlut.edu.cn/v1/search/full_text_files
    ?query={keyword}
    &root_id={root_id}
    &token={token}
```

参数和响应格式与 `search/files` 相同，区别在于匹配文件内容而不仅是文件名。`root_id` 同样优先使用 NAOSI 的 `ak7an4chdvtq`。

#### 搜索群组

```
GET http://pan.dlut.edu.cn/v1/search/groups
    ?query={keyword}
    &token={token}
    [&offset={offset}]
    [&limit={limit}]
```

参数说明：
- `query`: 搜索关键词。
- `token`: 登录获取的 token。
- 不需要 `root_id`。

返回包含 `total`、`offset`、`entries` 的结果集，entries 为群组信息列表。

### 5. 下载文件

```
GET http://pan.dlut.edu.cn/v1/roots/{root_id}/files/{file_id}
    ?token={token}
```

参数说明：
- `root_id`: 空间根目录 ID。
- `file_id`: 文件 ID，从 list_folder 或搜索结果中获取。
- `token`: 同上。

响应为文件二进制流，或 302 跳转到实际下载地址。

## 安全与隐私规则

- **不保存凭证**：账号、密码、token 只存在于单次请求内存中，不写入磁盘、不输出到日志或对话。
- **不批量抓取**：只在用户明确指定的路径或文件上操作。
- **有副作用操作需确认**：下载、删除、移动、上传等操作前必须再次确认。
- **公开与私有边界**：API 返回的元数据（文件名、大小、时间）可整理；文件正文、课件内容、试卷等私有资料未经明确授权不得复制或传播。

## 质量规则

- 不编造接口返回字段；如遇接口变更，以实际响应为准。
- 对时间敏感信息（token 有效期、目录结构）要求重新获取。
- 输出最小可用结果，不暴露其他用户隐私或群组内部资料。
