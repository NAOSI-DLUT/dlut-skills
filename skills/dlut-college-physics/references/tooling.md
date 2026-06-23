# 大学物理工具

## Python 科学计算
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import integrate, optimize

# 数值积分
result, error = integrate.quad(func, a, b)

# 解方程
root = optimize.fsolve(equation, x0)

# 画图
x = np.linspace(0, 10, 100)
y = np.sin(x)
plt.plot(x, y)
plt.show()
```

## MATLAB
```matlab
% 符号计算
syms x
f = x^2 + 2*x + 1;
diff(f, x);
int(f, x);

% 画图
x = linspace(0, 2*pi, 100);
y = sin(x);
plot(x, y);
```

## 在线资源
- WolframAlpha：公式计算、单位换算、常数查询
- PhET 模拟：httpsphet.colorado.edu/（物理交互仿真）
- GeoGebra：函数图像、几何作图

## 计算器
- 科学计算器：Casio fx-991CN X 等
- 注意有效数字和角度/弧度模式切换
