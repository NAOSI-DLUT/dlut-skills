---
name: dlut-cae
description: 面向大连理工大学可视化原理、前处理技术、CAE/几何处理相关课程的中文 skill。用于 zzzlib、MeshLib、TMeshLib、OpenGL/freeglut、半边网格、模型显示、法向、体积、纹理、复变函数可视化和 Visual Studio 工程调试。
---

# DLUT CAE

## 目标

沉淀大工可视化原理、前处理技术和 CAE/几何处理相关课程经验，尤其是公开资料较少的 `zzzlib`、`MeshLib`、`TMeshLib` 工程用法。

## 工作流

1. 先判断用户处理的是环境配置、网格结构、OpenGL 显示、算法实现、报告整理还是课程复习。
2. 查课程与作业索引用 `references/course-index.md`。
3. 查 Visual Studio/freeglut 配置用 `references/visual-studio-freeglut.md`。
4. 查 zzzlib 目录和数据格式用 `references/zzzlib-map.md`。
5. 查 MeshLib/TMeshLib 模式用 `references/meshlib-patterns.md`。
6. 查上机速查和复习建议用 `references/cheatsheet.md`、`references/review.md`。

## 质量规则

- 这类代码依赖旧式 OpenGL/freeglut/Visual Studio 工程，先尊重现有项目结构。
- 不大改框架；优先在课程要求的 `zzzlib/basic_meshviewer` 或指定文件中补功能。
- 提醒用户在 Release/x64、工作目录、DLL 路径、数据文件路径上做核验。
