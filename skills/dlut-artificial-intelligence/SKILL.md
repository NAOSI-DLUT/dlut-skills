---
name: dlut-artificial-intelligence
description: 面向大连理工大学人工智能课程的中文 skill。用于 TensorFlow/Keras、PyTorch、MNIST/FashionMNIST、CNN、训练/验证/测试划分、模型保存加载、自定义图片预测、notebook 调试和复习。
---

# DLUT Artificial Intelligence

## 目标

帮助用户完成 AI 课程 notebook、深度学习模型训练、图片预测、框架报错修复和复习整理。

## 工作流

1. 判断任务是 TensorFlow/Keras、PyTorch、数据集、训练报错、图片预测还是报告。
2. 课程索引读取 `references/course-index.md`。
3. 环境与 GPU/包安装读取 `references/tooling.md`。
4. 框架 API 速查读取 `references/cheatsheet.md`。
5. 报告和复习读取 `references/review.md`。

## 质量规则

- PyTorch、torchvision、TensorFlow API 变化较快；涉及当前语法时用 Context7/官方文档核验。
- 明确区分训练集、验证集、测试集和用户自定义图片。
- 不伪造 accuracy/loss；没有运行就说清楚。
