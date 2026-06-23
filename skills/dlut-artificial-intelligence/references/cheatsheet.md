# AI API 速查

## Keras

- `keras.Sequential([...])`：顺序模型。
- `model.compile(optimizer=..., loss=..., metrics=...)`。
- `model.fit(..., validation_data=...)`。
- `keras.callbacks.EarlyStopping(...)`。

## PyTorch

- `datasets.MNIST/FashionMNIST(root, train, download, transform)`：数据集。
- `DataLoader(dataset, batch_size, shuffle)`：批加载。
- `nn.Module`：定义模型。
- `torch.save(model.state_dict(), path)`：保存权重。
- `model.load_state_dict(torch.load(path))`：加载权重。
- `model.eval()`、`torch.no_grad()`：推理模式。
- `torch.softmax(output, dim=1)`：概率。
- `torch.argmax(probability)`：预测类别。

## 常见坑

- 忘记归一化。
- 输入维度缺少 batch 或 channel。
- 自定义图片黑白方向与训练数据不一致。
- CUDA/CPU 张量混用。
