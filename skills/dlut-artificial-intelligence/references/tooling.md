# AI 工具链

- 推荐 Python 虚拟环境 + Jupyter/VS Code。
- 常用包：`numpy`, `pandas`, `matplotlib`, `scikit-learn`, `tensorflow`, `torch`, `torchvision`, `Pillow`。
- PyTorch 设备选择常见写法：`torch.device("cuda" if torch.cuda.is_available() else "cpu")`。
- 数据集下载可能受网络影响，可提前配置镜像或手动下载。

## 调试建议

- 打印张量形状。
- 确认模型和输入在同一 device。
- 训练循环记录 train/val loss。
- 推理时使用 `model.eval()` 和 `torch.no_grad()`。
