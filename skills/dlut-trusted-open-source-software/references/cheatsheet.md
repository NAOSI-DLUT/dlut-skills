# Rust/开源库速查

- `serde`/`serde_json`：序列化。
- `clap`：命令行参数。
- `tokio`：异步运行时，`#[tokio::main]`、`tokio::spawn`、`TcpListener`。
- `reqwest`：HTTP 客户端。
- `SurrealDB`：本地知识库；实验可使用 `kv-mem` 降低原生编译负担。
- `candle`、`tokenizers`、`hf-hub`：本地模型推理和 HuggingFace 模型加载。
- `Arc`, `Mutex`, `mpsc`：多线程共享和通信。

## 常见坑

- borrow checker 报错时先缩短借用作用域。
- async 函数忘记 `.await`。
- `Send/Sync` 限制导致任务不能跨线程。
- Windows 下原生库链接失败。
