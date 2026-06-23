---
name: dlut-signals-systems
description: 面向大连理工大学信号与系统课程的中文 skill。用于连续/离散信号、傅里叶变换、拉普拉斯变换、Z 变换、系统响应、卷积、滤波器分析和复习。
---

# DLUT Signals and Systems

## 目标

帮助用户理解信号与系统理论、完成变换计算、分析系统特性（线性/时不变/因果/稳定）、使用 Python/MATLAB 验证和复习。

## 工作流

1. 识别主题：信号分类、系统性质、时域分析、频域分析、傅里叶变换、拉普拉斯变换、Z 变换或采样定理。
2. 课程索引读取 `references/course-index.md`。
3. 计算工具读取 `references/tooling.md`。
4. 变换对/性质速查读取 `references/cheatsheet.md`。
5. 复习要点读取 `references/review.md`。

## 质量规则

- 变换计算要标明收敛域、变换对和所用性质（时移、频移、卷积定理等）。
- 系统分析要先判断线性、时不变性、因果性和稳定性。
- 卷积计算要给出图形翻转-平移-相乘-积分/求和的步骤。
- Python/MATLAB 代码要区分连续近似和离散实现，并说明采样率影响。
