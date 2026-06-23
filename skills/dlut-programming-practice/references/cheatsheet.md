# EasyX 速查

- `initgraph(w,h)`：初始化窗口。
- `closegraph()`：关闭窗口。
- `BeginBatchDraw()` / `FlushBatchDraw()` / `EndBatchDraw()`：双缓冲。
- `cleardevice()`：清屏。
- `setfillcolor`, `solidcircle`, `solidrectangle`, `line`：绘制。
- `ExMessage`、`peekmessage`：事件处理。
- `GetTickCount()`：帧率控制。
- `GetLocalTime(&time)`：系统时间。
- `loadimage`, `putimage`：加载和绘制图片。

## 游戏循环

1. 处理输入。
2. 更新状态。
3. 碰撞检测。
4. 绘制画面。
5. 控制帧率。
