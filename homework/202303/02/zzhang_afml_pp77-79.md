# AFML: pp 77-79

### 5.4 The method

- 这里也用了$B$来表示 backshift operator：$B^kX_t = X_{t-k}$ 回到 k 天前
- 满足分配律$(1-B)^2X_t=X_t - 2X_{t-1}+X_{t-2}$
- Binomial series 挺简单的就是分配律+combinatorial法则
    - $(1-B)^d=\sum_{k=0}^\infty\binom{d}{k}(-B)^k=1-dB+\frac{d(d-1)}{2!}B^2-\frac{d(d-1)(d-2)}{3!}B^3+\cdots$ 这里的$d$ 只是一个数字，不是表示极小量

#### 5.4.1 Long Memory

- 给上面那个binomial series前的系数一个符号
    - $\tilde{X}_t=\sum_{k=0}^\infty w_kX_{t-k}$
    - $w=\{1,-d,\frac{d(d-1)}{2!},-\frac{d(d-1)(d-2)}{3!},\cdots,(-1)^k\prod_{i=0}^{k-1}\frac{d-i}{k!},\cdots\}$
    - $X=\{X_t,X_{t-1},X_{t-2},X_{t-3},\cdots,X_{t-k},\cdots\}$
- 可以画一个横坐标为 $k$ 纵坐标为 $w_k$ 的图，可以发现 $d$ 越大，$w$ 恒为 0得越早 （k 越小）
    - $\prod_{i=0}^{k=1}\frac{d-i}{k!}=0, \forall k> d$  就叫做 memory is cancelled 

#### 5.4.2 Iterative Estimation

- 从上面那个$w_k$ 的计算过程（其实就是组合数）可以得到递推式）
    - $w_k=-w_{k-1}\frac{d-k+1}{k}$
- $d\in[0,1]$ 的时候，所有$w_k$ 除了$w_0=1$外都小于零，且在$w_1$取到最小值（最小值大于等于-1）
- $d\in[1,2]$的时候，$w_0=0$, $-2.0\le w_1 < 0$, 而 $0 \le w_k < 1, \forall k > 2$

