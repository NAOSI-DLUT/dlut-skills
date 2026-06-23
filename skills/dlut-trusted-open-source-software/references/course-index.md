# 课程索引

来源仓库：`D:/Projects/dlut-homework/trusted-open-source-software`

## 主题

- `course/examples`：ownership、reference、multi_threading、fork 等 Rust 示例。
- lab1-lab3：Rust 基础和图/可视化相关实验。
- lab4：chatbot/RAG，SurrealDB、本地 embedding、Candle、HuggingFace 模型、命令行。
- lab5：Rust HTTP server，单线程、多线程线程池、Tokio async、benchmark。

## 特别经验

- Windows 下 SurrealDB RocksDB 后端可能触发 zstd-sys/libclang/原生编译问题；实验验证可改用 `kv-mem`。
- 国内网络访问 HuggingFace 可能超时，需要提前下载或配置可用网络。
