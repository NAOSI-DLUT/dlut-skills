# Python 工具链

- 推荐 Python 虚拟环境 + Jupyter/VS Code。
- 常用包：`numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`。
- notebook 运行前确认当前工作目录和数据文件路径。
- 大量 HTML 输出可清理，但不要删掉关键结果和图。

## 调试建议

- 用 `df.head()`, `df.info()`, `df.describe()` 先看数据。
- 用 `random_state` 固定划分和模型随机性。
- 分类任务输出混淆矩阵和分类报告。
- 回归任务输出 MSE/RMSE/R2 和残差图。
