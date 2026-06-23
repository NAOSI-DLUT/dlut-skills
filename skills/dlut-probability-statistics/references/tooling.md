# 概率论与数理统计工具

## Python
```python
import numpy as np
import scipy.stats as stats
import matplotlib.pyplot as plt

# 概率密度/质量函数
stats.norm.pdf(x, loc=μ, scale=σ)
stats.binom.pmf(k, n, p)

# 分布函数
stats.norm.cdf(x, loc=μ, scale=σ)

# 随机抽样
stats.norm.rvs(loc=μ, scale=σ, size=100)

# 分位数
stats.norm.ppf(0.975)  # 双侧 95% 对应 1.96
```

## R 语言
```r
# 概率密度/分布/分位数/随机数
dnorm(x, mean, sd)
pnorm(q, mean, sd)
qnorm(p, mean, sd)
rnorm(n, mean, sd)
```

## 计算器/在线工具
- WolframAlpha：概率计算、积分、画图
- GeoGebra：概率分布可视化
