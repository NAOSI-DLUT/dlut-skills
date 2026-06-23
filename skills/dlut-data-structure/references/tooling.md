# 工具链

- 多数为 C++ 单文件或少量头源文件。
- 单文件：`g++ file.cpp -std=c++17 -Wall -Wextra -o file`。
- 多文件题如 spellchecking，要同时编译 `main.cpp hashset.cpp`。
- 使用小样例验证，再用边界样例覆盖空输入、重复值、极端长度。
