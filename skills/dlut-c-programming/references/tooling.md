# 工具链

- 推荐使用 GCC/Clang 或 Visual Studio C 工程。
- 单文件题可用 `gcc file.c -Wall -Wextra -std=c11 -o file` 编译。
- Windows 下注意控制台编码和换行；中文输出可简化为英文提示。
- 调试时先准备 3 类样例：普通、边界、非法/极端输入。

## 常见编译问题

- 忘记包含头文件，如 `stdio.h`、`math.h`、`string.h`。
- 使用 `sqrt` 等数学函数时在类 Unix 环境需链接 `-lm`。
- 数组长度不够或未初始化。
- `scanf` 格式与变量类型不匹配。
