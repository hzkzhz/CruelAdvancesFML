# AFML: pp 93-94

## Ch 6 Ensemble Methods

介绍两种ensemble方法，主要关注可能的错误(error)。

#### 6.2 The three source or errors

主要有三个错误(error)：

1. Bias: 主要由于 unrealistic assumptions => underfit
2. Variance: mistaken noise with signal => overfit
3. Noise: 比如unpredictable changes, measurement errors. 不能被任何模型解释



假设有$y=f[x]+\epsilon$，用$\hat{f}[x]$ 去fit $f[x]$

$$E[(y_i-\hat{f}[x_i])^2]=(\underbrace{(E[\hat{f}[x_u]-f[x_i]])}_{bias})^2+\underbrace{Var[\hat{f}[x_i]]}_{variance}+\underbrace{\sigma_\epsilon^2}_{noise}$$

