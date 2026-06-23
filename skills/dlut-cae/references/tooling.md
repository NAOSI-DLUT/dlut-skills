# 工具链

- 主要环境：Windows + Visual Studio + 课程给定 `.sln/.vcxproj`。
- 常见依赖：freeglut、OpenGL、stb_image、课程内 `zzzlib`。
- 运行建议：优先 Release 模式，确认平台 x64；不要随意移动 `zzzlib`、`zzzdata`、`zzzbin`。
- 数据文件常见扩展：`.m` 表面网格、`.t` 四面体网格、`.bmp/.jpg/.png` 纹理。

## 调试优先级

1. 工程能否编译。
2. DLL 是否能被找到。
3. 数据文件相对路径是否正确。
4. 鼠标/键盘回调是否触发。
5. OpenGL 状态是否被前一段绘制污染。
