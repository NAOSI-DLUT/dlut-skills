# C 语言速查

- 输入输出：`scanf`, `printf`, `getchar`, `putchar`, `fgets`。
- 数学：`abs`, `fabs`, `sqrt`, `pow`, `sin`, `cos`。
- 字符串：`strlen`, `strcmp`, `strcpy`, `strcat`, `strstr`。
- 排序：冒泡、选择、插入；注意比较方向和循环边界。
- 递归：明确终止条件和递推式。
- 结构体：`typedef struct { ... } Name;`。
- 链表：创建节点、尾插、遍历、释放。

## 易错点

- 字符串数组要留 `'\0'`。
- `scanf("%s", s)` 不能读空格。
- 整数除法会截断。
- `for` 循环上界常见 off-by-one。
- 闰年：能被 4 整除且不能被 100 整除，或能被 400 整除。
