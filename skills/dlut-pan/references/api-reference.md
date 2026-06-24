# 大工云盘 API 参考

## 基础信息

- API 基础地址：`http://pan.dlut.edu.cn/v1`
- Token 获取地址：`http://202.118.66.144:8088/v1/auth/sign_in`
- 所有后续请求需在 Query 参数中携带 `token`。

---

## 1. 登录获取 Token

### 请求

```http
POST http://202.118.66.144:8088/v1/auth/sign_in?link_device={device}&password={password}&link_name={link_name}&ldap_name={ldap_name}&username={username}
Content-Length: 0
```

> 注意：参数通过 query string 传递，body 必须为空。

### 参数

| 参数名       | 类型   | 必填 | 说明                     |
|--------------|--------|------|--------------------------|
| `username`   | string | 是   | 学号/工号                |
| `password`   | string | 是   | 统一身份认证密码         |
| `link_device`| string | 是   | 设备标识（如手机型号）   |
| `link_name`  | string | 是   | 设备名称                 |
| `ldap_name`  | string | 是   | LDAP 名称，通常同设备名  |

### 响应示例

```json
{
  "token": "{token}",
  "user_id": "...",
  ...
}
```

提取 `token` 字段用于后续请求。

---

## 2. 加入群组

### 请求

```http
POST http://pan.dlut.edu.cn/v1/users/{user_id}/groups?group_id={group_id}&token={token}
Content-Type: application/json

{"remarks": "申请理由"}
```

> 注意：`group_id` 是群组 ID，不是 `root_id`。

### 参数

| 参数名    | 类型   | 必填 | 说明                     |
|-----------|--------|------|--------------------------|
| `user_id` | string | 是   | 用户 ID                  |
| `group_id`| string | 是   | 群组 ID                  |
| `token`   | string | 是   | 登录获取的 token         |
| `remarks` | string | 否   | 申请备注（放在 body 中） |

### 响应示例

```json
{
  "relation": {
    "is_activated": true,
    "role": { "name": "member", "display_value": "成员" }
  }
}
```

- 若 `relation.is_activated` 为 `true`，说明该群组为公开群，用户**直接加入成功**。
- 若 `relation.is_activated` 为 `false`，说明需要群主审批，用户状态为"审批中"。

### NAOSI 资料云盘

- 群组 ID：`ej7f8s176d8f`
- 空间 root_id：`ak7an4chdvtq`

---

## 3. 列出目录

### 请求

```http
POST http://pan.dlut.edu.cn/v1/fileops/list_folder?root_id={root_id}&path={path}&token={token}&locale=zh_CN
Content-Length: 0
```

> 注意：参数通过 query string 传递，body 必须为空。

### 参数

| 参数名    | 类型   | 必填 | 说明                     |
|-----------|--------|------|--------------------------|
| `root_id` | string | 是   | 空间根目录 ID            |
| `path`    | string | 是   | 目录路径，根目录为 `/`   |
| `token`   | string | 是   | 登录获取的 token         |
| `locale`  | string | 否   | 语言区域，如 `zh_CN`     |

### 示例

```http
POST http://pan.dlut.edu.cn/v1/fileops/list_folder?root_id={root_id}&path=%2F&token={token}&locale=zh_CN
Content-Length: 0
```

### 响应

目录列表，包含文件/文件夹的元数据：
- `name`: 名称
- `type`: 类型（文件/目录）
- `size`: 大小
- `modified`: 更新时间
- `path`: 路径
- `id`: 文件/目录 ID

---

## 3. 下载文件

### 请求

```http
GET http://pan.dlut.edu.cn/v1/roots/{root_id}/files/{file_id}?token={token}
```

### 参数

| 参数名    | 类型   | 必填 | 说明                     |
|-----------|--------|------|--------------------------|
| `root_id` | string | 是   | 空间根目录 ID            |
| `file_id` | string | 是   | 文件 ID                  |
| `token`   | string | 是   | 登录获取的 token         |

### 示例

```http
GET http://pan.dlut.edu.cn/v1/roots/{root_id}/files/{file_id}?token={token}
```

### 响应

文件二进制流，或 302 重定向到实际下载地址。

---

## 4. 搜索

### 4.1 搜索文件名

#### 请求

```http
GET http://pan.dlut.edu.cn/v1/search/files?query={query}&root_id={root_id}&token={token}
```

#### 参数

| 参数名    | 类型   | 必填 | 说明                       |
|-----------|--------|------|----------------------------|
| `query`   | string | 是   | 搜索关键词                 |
| `root_id` | string | 是   | 空间根目录 ID              |
| `token`   | string | 是   | 登录获取的 token           |
| `path`    | string | 否   | 限制到某个路径             |
| `offset`  | int    | 否   | 分页偏移，默认 0           |
| `limit`   | int    | 否   | 分页大小                   |

> `root_id` 必须提供，否则返回 403。

#### 响应

```json
{
  "total": 20,
  "offset": 0,
  "entries": [
    {
      "id": "...",
      "root_id": "...",
      "path": "/...",
      "name": "...",
      "is_dir": false,
      "size": {"bytes": 111987, "display_value": "109.36 KB"},
      ...
    }
  ]
}
```

---

### 4.2 搜索全文

#### 请求

```http
GET http://pan.dlut.edu.cn/v1/search/full_text_files?query={query}&root_id={root_id}&token={token}
```

#### 参数

与 `search/files` 相同，必填 `query`、`root_id`、`token`。

#### 响应

格式与 `search/files` 相同：
```json
{
  "total": 20,
  "offset": 0,
  "entries": [...]
}
```

---

### 4.3 搜索群组

#### 请求

```http
GET http://pan.dlut.edu.cn/v1/search/groups?query={query}&token={token}
```

#### 参数

| 参数名    | 类型   | 必填 | 说明                       |
|-----------|--------|------|----------------------------|
| `query`   | string | 是   | 搜索关键词                 |
| `token`   | string | 是   | 登录获取的 token           |
| `offset`  | int    | 否   | 分页偏移，默认 0           |
| `limit`   | int    | 否   | 分页大小                   |

> 搜索群组不需要 `root_id`。

#### 响应

```json
{
  "total": 3,
  "offset": 0,
  "entries": [
    {
      "id": "...",
      "root_id": "...",
      "name": "操作系统实验课2024",
      "type": {"name": "public", "display_value": "Public (anyone can join freely)"},
      "intro": "...",
      "user_count": 84,
      ...
    }
  ]
}
```

---

## 历史接口变更记录

- 2026-06-23: 补充 `sign_in` 接口地址 `http://202.118.66.144:8088/v1/auth/sign_in`，确认 `list_folder` 和文件下载接口格式。
- 此前入口为 `http://pan.dlut.edu.cn/` 配合浏览器 SSO 登录；现可直接通过 API 获取 token。
