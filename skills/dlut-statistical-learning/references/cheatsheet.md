# R 速查

## 数据与基础

- `library(pkg)`：加载包。
- `data(Name)`：加载包内数据集。
- `str(df)`, `summary(df)`, `pairs(df)`：探索数据。
- `set.seed(1)`：固定随机性。

## 模型

- `lm(y ~ x1 + x2, data=df)`：线性回归。
- `glm(y ~ x, data=df, family=binomial)`：逻辑回归。
- `predict(fit, newdata=..., type="response")`：预测概率。
- `table(pred, truth)`：混淆矩阵。
- `cv.glm(data, fit, K=...)`：交叉验证。
- `boot(data, statistic, R=...)`：bootstrap。
- `regsubsets()`：子集选择。
- `cv.glmnet()`：ridge/lasso 交叉验证。
- `tree()`, `cv.tree()`, `prune.misclass()`：分类树。
- `randomForest(..., importance=TRUE)`：随机森林和变量重要性。
- `svm()`, `tune()`：SVM 和调参。
- `gam()`, `s()`, `bs()`：GAM 和样条。

## 常见坑

- 分类标签要转成 factor。
- 训练/测试划分后不要把测试集信息泄露进训练。
- `predict.glm` 默认返回 link scale，概率要 `type="response"`。
- `glmnet` 需要模型矩阵 `model.matrix()`，不是普通 data frame。
