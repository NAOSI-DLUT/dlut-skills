---
name: dlut-machine-learning
description: 面向大连理工大学机器学习课程的中文 skill。用于 Python notebook、numpy/pandas/matplotlib/scikit-learn、线性回归、逻辑回归、决策树、训练测试划分、评估指标、API 警告修复、作业检查和复习。
---

# DLUT Machine Learning

## 目标

帮助用户完成机器学习课程 notebook、数据处理、模型训练、结果解释、API 兼容性修复和复习整理。

## 工作流

1. 判断任务是数据读取、模型实现、notebook 报错、结果解释还是复习。
2. 课程索引读取 `references/course-index.md`。
3. Python/Jupyter 环境读取 `references/tooling.md`。
4. API 速查读取 `references/cheatsheet.md`。
5. 报告和复习读取 `references/review.md`。

## 质量规则

- 不伪造模型指标；没有运行时只给代码模板和解释方法。
- scikit-learn API 会变化；遇到弃用警告或参数问题时用 Context7 查当前文档。
- 输出要包含数据划分、模型参数、评价指标和解释。
