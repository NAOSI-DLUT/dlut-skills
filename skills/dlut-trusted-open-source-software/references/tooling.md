# Rust 工具链

- 安装 Rust stable：`rustup`, `cargo`, `rustc`。
- 常用命令：`cargo run`, `cargo test`, `cargo fmt`, `cargo clippy`。
- Windows 涉及原生依赖时确认 MSVC Build Tools、clang/libclang、环境变量。
- 大模型/embedding 项目要注意缓存目录、网络和磁盘空间。

## 调试建议

- 先 `cargo check` 看类型错误。
- feature 变更后 `cargo tree -e features` 排查依赖。
- 并发 server 先本地小并发测试，再做 benchmark。
