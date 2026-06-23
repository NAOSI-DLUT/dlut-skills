# 信号与系统工具

## Python (NumPy + SciPy + Matplotlib)
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

# 系统分析
sys = signal.TransferFunction([1], [1, 2, 1])
w, H = signal.freqresp(sys)

# 卷积
y = np.convolve(x, h)

# FFT
X = np.fft.fft(x)
freq = np.fft.fftfreq(len(x), d=dt)
```

## MATLAB
```matlab
% 卷积
y = conv(x, h);

% 傅里叶变换
X = fft(x);

% 系统分析
sys = tf([1], [1 2 1]);
bode(sys);

% Z 变换（Symbolic Math Toolbox）
syms z n
iztrans(z/(z-0.5), z, n);
```

## 在线工具
- WolframAlpha：积分、变换计算
- Desmos：函数画图
