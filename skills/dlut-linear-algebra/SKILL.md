---
name: dlut-linear-algebra
description: 面向大连理工大学线性代数课程的中文学习 skill。用于线代复习、MATLAB 上机、矩阵运算、行列式、逆矩阵、秩、特征值、QR/SVD、数值验证、作业检查和考试复习。
---

# DLUT Linear Algebra

## 目标

帮助用户完成线性代数课程复习、MATLAB 上机、代码查错、概念解释和题型整理。

## 工作流

1. 判断任务是理论题、MATLAB 上机、代码错误、复习计划还是报告整理。
2. 查题型索引用 `references/course-index.md`。
3. 查环境与 MATLAB 运行习惯用 `references/tooling.md`。
4. 查函数和数值验证方式用 `references/cheatsheet.md`。
5. 查复习与报告建议用 `references/review.md`。

## 质量规则

- 优先解释矩阵意义和计算步骤，再给 MATLAB 代码。
- 数值验证用容差，例如 `norm(A-B) < 1e-10`，不要用浮点数直接相等。
- 涉及 MATLAB 当前语法和工具箱时使用 Context7/MathWorks 文档核验。
