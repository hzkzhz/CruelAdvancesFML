# AFML: pp 141-142

## Ch 10: Bet Sizing

- 更多的PM是poker player than chess player，有一个点就poker还会注重bet sizing

10.2 Strategy-independent bet sizing approaches

- $m_{i,t}\in[-1,1]$: bet size strategy $i$ at time $t$

我们更愿意以这样的方式调整头寸规模，即我们为交易信号在减弱之前增强的可能性保留一些现金。

- 第一种方法是计算序列$c_t=c_{t,l}-c_{t,s}$ 其中$c_{t,l}$ 是 t时刻的concurrent long bet number at time t. $c_{t,s}$ 是concurrent short bet number

    - fit a mixture of two Gaussian on $\{c_t\}$，并使用一个方法，然后bet size如下：

    $$m_t=\frac{F[c_t]-F[0]}{1-F[0]}\text{ if } c_t \ge 0; \frac{F[c_t]-F[0]}{F[0]} \text{ if } c_t < 0$$

    - $F[x]$ 是CDF of fiited mixture of two Gaussians for a value x.
        - 当预测到更好的signal的概率为0.1时，我们设置bet size为0.9.

- 第二种方法是用budgeting approach

    - concurrent long bets number 的最大值为 $\max_i\{c_{i,l}\}$ ；concurrent short bets number 的最大值为 $\max_i\{c_{i,s}\}$
    - 则使用 bet size: $m_t=c_{t,l}\frac{1}{\max_i\{c_{i,l}\}}-c_{t,s}\frac{1}{\max_i\{c_{i,s}\}}$ 

- 第三种方法是用 meta-labeling

    - 用SVC或者RF训练一个分类器，输出错误分类的概率，用这个概率来决定bet size
