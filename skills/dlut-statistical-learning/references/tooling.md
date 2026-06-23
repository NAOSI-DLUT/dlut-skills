# R 工具链

## 推荐环境

- 安装 R 和 RStudio，或 VS Code + R 扩展。
- 首次运行前安装课程常用包：`ISLR`, `MASS`, `boot`, `class`, `leaps`, `glmnet`, `pls`, `splines`, `mgcv`, `tree`, `randomForest`, `rpart`, `rpart.plot`, `gbm`, `e1071`。
- 用 `set.seed()` 保证训练/测试划分可复现。

## 运行建议

- 每个脚本开头写清 `library(...)` 和 `data(...)`。
- 对分类问题输出 `table(Pred=..., Truth=...)` 和错误率。
- 对回归问题输出 MSE、残差图、`summary()` 关键解释。
- 对作业报告不要只贴代码，要解释统计意义。
