# MATLAB 工具链

## 推荐环境

- 安装 MATLAB 和 Symbolic Math Toolbox。
- 在 VS Code 中可安装 MATLAB 相关扩展，用于语法高亮、片段、运行脚本或连接 MATLAB。具体扩展名称和能力可能变化，使用前查 VS Code Marketplace 与 MathWorks 文档。
- `.m` 文件建议按题号保存，如 `q1.m`、`q2.m`，每题输出前加简短说明。

## 常见运行建议

- 符号计算前写 `syms x y t n`。
- 绘图脚本中用 `figure` 分开图窗，避免覆盖。
- 三维绘图先检查定义域，例如 `sqrt(x.^2-y.^2)` 可能产生复数或 `NaN`。
- 用 `simplify`、`vpa`、`double` 在符号结果和数值结果之间转换。

## 核验

涉及函数语法、工具箱安装、VS Code 插件能力时，优先查 MathWorks 当前文档。
