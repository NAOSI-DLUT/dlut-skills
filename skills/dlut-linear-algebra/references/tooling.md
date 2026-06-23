# MATLAB 工具链

- 安装 MATLAB；如需符号矩阵或精确表达式，确认 Symbolic Math Toolbox 可用。
- VS Code 可配 MATLAB 扩展做编辑；复杂调试仍建议 MATLAB Desktop。
- 输出结果时用 `disp("rank(A)="); disp(rank(A));` 这类清晰标签。
- 上机脚本开头可 `clear; clc;`，但调试时避免清掉需要检查的变量。

## 数值习惯

- 验证等式用 `norm(lhs-rhs) < 1e-10`。
- 求线性方程优先 `A\b`，解释逆矩阵时才使用 `inv(A)`。
- 随机矩阵题建议固定 `rng(seed)`，便于复现。
