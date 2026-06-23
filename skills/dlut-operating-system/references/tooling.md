# 工具链

- Linux/WSL 环境优先。
- pthread 程序编译：`gcc file.c -pthread -o file`。
- C++ 实验：`make` 或 `g++ ...`，按 Makefile 为准。
- System V IPC 程序运行后注意清理共享内存和信号量，避免残留影响下次测试。

## 调试建议

- 每个系统调用检查返回值。
- 并发输出加进程/线程 ID。
- 页面置换和磁盘调度准备经典测试序列。
