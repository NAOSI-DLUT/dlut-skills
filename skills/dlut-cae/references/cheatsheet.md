# CAE 速查

## OpenGL/freeglut

- `glBegin(GL_LINES/GL_POINTS/GL_POLYGON)` 与 `glEnd()` 成对出现。
- `glColor3f(r,g,b)` 设置颜色。
- `glVertex3d(x,y,z)` 输出顶点。
- `glNormal3d(nx,ny,nz)` 设置法向。
- `glEnable(GL_TEXTURE_2D)` 开启纹理。
- `glTexCoord2d(u,v)` 设置纹理坐标。
- `glutDisplayFunc`、`glutMouseFunc`、`glutMotionFunc`、`glutKeyboardFunc` 注册回调。

## 常用公式

- z 值着色：若模型 z 范围约为 `[-1,1]`，可用红蓝渐变 `glColor3f(-z/2+1, 0, z/2+1)`。
- 法向可视化：从顶点 `p` 画到 `p + scale * normal`。
- 封闭三角网格体积：对每个三角面累加 `dot(p1, cross(p2, p3)) / 6`，最后取绝对值或根据朝向解释符号。

## 常见坑

- 头文件大小写不一致，如 `Point2.H` 与 `Point2.h`。
- Debug/Release 平台配置不一致。
- DLL 不在运行目录或 PATH。
- OpenGL 即时模式状态残留，绘制后要恢复必要状态。
