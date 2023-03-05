# AFML: p80

#### 5.5 Implementation

两个：Expanding window 和 fixed-width window fracdiff (FFD)

回顾：$\tilde{X}_t=\sum_{k=0}^{\infty} w_kX_{t-k}$

#### 5.5.1 Expanding Window

- $\tilde{X}_{T-l}$ （用了$w_0,\cdots,w_{T-l-1}$）用到的weights 比 $\tilde{X}_{T}$ (用了$w_0,\cdots,w_{T-1}$)的要少 $l$ 个
- 引入 weight-loss: $\lambda_l = \frac{\sum_{j=T-l}^T|w_j|}{\sum_{i=0}^{T-1}|w_i|}$ 分子就是少的部分，分母是所有的部分

- 给定一个tolerance $\tau\in[0,1]$，我们可以找到一个点$l^*$，使得$\lambda_{l^*}\le\tau < \lambda_{l^*+1}$
    - $l^*$ 表示它和比它久远的$\tilde{X}_t$ 超过tolerance了
- $\lambda_{l^*}$ 和序列${w_k}$的收敛速度有关 => 和 $d\in[0,1]$有关，d 越小，$l^*$ 越大

这个图没看懂。
