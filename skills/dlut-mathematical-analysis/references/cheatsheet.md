# MATLAB 速查

## 符号计算

- `syms x y n t`：定义符号变量。
- `limit(f,x,a)`：求极限；左右极限用 `'left'`、`'right'`。
- `diff(f,x)`：求导；`diff(f,x,2)` 求二阶导。
- `int(f,x)`：不定积分；`int(f,x,a,b)` 定积分。
- `solve(eq,var)`：解方程或方程组。
- `simplify(expr)`：化简表达式。

## 绘图

- `plot(x,y)`：二维曲线。
- `polarplot(theta,rho)`：极坐标曲线。
- `plot3(x,y,z)`：空间曲线。
- `[x,y]=meshgrid(a:h:b)`：生成网格。
- `surf(x,y,z)`：三维曲面。
- `xlabel/ylabel/zlabel/title/grid on`：图形标注。

## 易错点

- 数组运算用 `.^`、`.*`、`./`，不要误用矩阵运算符。
- 符号函数和数值数组不要混在同一个表达式里。
- 曲面题先判断定义域，必要时用 `real`、`isreal` 或遮罩过滤。
