# EasyX/Visual Studio 工具链

- Windows + Visual Studio + EasyX。
- `#include <graphics.h>` 是 EasyX 入口。
- 确认 EasyX 已安装到对应 Visual Studio 版本。
- 工程中贴图和音频资源建议放固定 `assets` 目录，并用相对路径读取。

## 常见问题

- 找不到 `graphics.h`：EasyX 未安装或 VS 版本不匹配。
- 图片加载失败：工作目录不对。
- 画面闪烁：未使用双缓冲或清屏位置不对。
- CPU 占用高：主循环没有帧率控制。
