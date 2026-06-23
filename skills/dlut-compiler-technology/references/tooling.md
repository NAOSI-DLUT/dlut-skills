# 工具链

- C++ 实验可用 `g++ main.cpp -std=c++17 -Wall -Wextra -o main`。
- lex/flex 实验在 Windows 下可使用 WSL、MSYS2 或课程指定环境。
- 输入文件通常为 `input.txt`，运行前确认工作目录。

## 常见问题

- 结束符 `$`、`#` 混用。
- epsilon 表示不统一。
- token 化时把 `id` 拆成字符。
- FIRST/FOLLOW 迭代没有直到不动点。
- SLR reduce 项没有按 FOLLOW 集填表。
