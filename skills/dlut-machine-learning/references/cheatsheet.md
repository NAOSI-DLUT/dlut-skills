# 机器学习 API 速查

- `pd.read_csv(path)`：读数据。
- `train_test_split(X,y,test_size=...,random_state=...)`：划分数据。
- `LinearRegression()`：线性回归。
- `LogisticRegression()`：逻辑回归；旧 notebook 中 `multi_class` 可能触发弃用警告，按当前 scikit-learn 文档调整。
- `DecisionTreeRegressor/Classifier(max_depth=...)`：决策树。
- `confusion_matrix`, `classification_report`：分类评估。
- `mean_squared_error`, `r2_score`：回归评估。
- `cross_val_score`：交叉验证。
- `StandardScaler`：标准化。

## 常见坑

- 训练/测试泄漏。
- 类别变量未编码。
- 特征尺度差异导致模型收敛慢。
- 忘记处理缺失值。
- 只看 accuracy，不看类别不平衡。
