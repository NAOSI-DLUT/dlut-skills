# Visual Studio/freeglut 配置

## 检查项

- 使用课程 `.sln` 打开，不要新建空项目后手动搬文件。
- 配置选择 Release，平台优先 x64；如工程只给 Win32，再按工程默认。
- `IncludePath` 应包含课程 `zzzlib/freeglut`。
- `LibraryPath` 应包含 `zzzlib/freeglut`。
- 链接依赖包含 `freeglut.lib`。
- 运行目录能找到 `freeglut.dll`，通常来自 `zzzbin` 或 `zzzlib/freeglut`。

## 常见错误

- `cannot open include file glut.h`：include 路径不对。
- `cannot open file freeglut.lib`：library 路径或平台不对。
- 程序启动提示缺少 DLL：运行目录或 PATH 找不到 `freeglut.dll`。
- 模型加载失败：工作目录不是项目目录，导致相对路径指向错误。

## 建议

- 先运行老师给的 basic 工程。
- 再复制同一项目配置到作业工程。
- 修改代码前保存一份能运行的基线。
