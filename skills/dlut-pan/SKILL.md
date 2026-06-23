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

## API 参考

详细接口定义见 `references/api-reference.md`。

## 工作流

### 1. 获取 token

使用 `POST` 请求，参数放在 query string 中，body 为空：

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

### 2. 列出目录

```
POST http://pan.dlut.edu.cn/v1/fileops/list_folder
    ?root_id={root_id}
    &path={path}
    &token={token}
    &locale=zh_CN

Content-Length: 0
```

参数说明：
- `root_id`: 空间根目录 ID，如个人空间 `{root_id}`。
- `path`: 目录路径，根目录传 `%2F`（即 `/`）。
- `token`: 上一步获取的 token。

返回目录列表，字段通常包括：文件/目录名、类型、大小、更新时间、路径等。

### 3. 搜索

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
- `root_id`: 空间根目录 ID（必填，否则返回 403）。
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

参数和响应格式与 `search/files` 相同，区别在于匹配文件内容而不仅是文件名。

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

### 4. 下载文件

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
