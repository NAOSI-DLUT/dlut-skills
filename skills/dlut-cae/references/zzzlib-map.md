# zzzlib 地图

## visualization-principle

- `zzzlib/freeglut`：freeglut 头文件、库和 DLL。
- `zzzlib/viewer`、`zzzlib/basic_opengl`：基础 OpenGL viewer、Arcball、Point、quat、stb_image。
- `zzzlib/MeshLib`：表面网格半边结构。
- `zzzlib/TMeshLib`：四面体网格结构。
- `zzzlib/basic_example`：表面网格示例。
- `zzzlib/basic_example_TMesh`：四面体网格示例。
- `zzzlib/basic_meshviewer`：课程作业主要扩展位置，含绘制、交互、预处理、属性计算。
- `zzzdata`：测试模型和纹理。
- `zzzbin`：运行所需 DLL。

## pre-processing-technology

- `zzzlib/MeshLib`：几何、解析器、半边网格核心。
- `zzzlib/basic_example`：拓扑操作和网格处理示例。
- `zzzdata/basic_example`：`eight.m`、`face.m`、`quadmesh.m` 等数据。

## 使用建议

- 不要把两个课程的 `zzzlib` 混用，先确认当前工程引用的是哪个目录。
- 修改前记录原文件职责；新增功能优先放入课程要求的 viewerDraw、keyInter 或 Tool 类。
