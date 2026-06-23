# MeshLib/TMeshLib 模式

## 表面网格

- 常见类：`CVertex`、`CEdge`、`CHalfEdge`、`CFace`、`CBaseMesh`。
- 常见迭代器：`MeshVertexIterator`、`MeshFaceIterator`、`FaceVertexIterator`、`VertexVertexIterator`。
- 顶点坐标通常通过 `pV->point()` 访问，返回 `CPoint`。
- 法向通常通过 `pV->normal()` 或课程属性计算模块获得。

## 四面体网格

- TMeshLib 增加 `CTVertex`、`CTEdge`、`CHalfFace`、`CTet` 等概念。
- 示例 `basic_example_TMesh` 定义派生类型并 typedef 出 `CTTMesh`。
- 处理四面体时要区分表面 face 与体 tet。

## 实现策略

- 先找到课程示例中已有的 iterator 写法，复制遍历框架再改内部逻辑。
- 对几何量计算，先在简单模型上验证，如 `eight.m` 或 `kitten.t`。
- 对保存文件，保留原始数据另存为 `_re` 或作业要求命名，避免覆盖输入。
