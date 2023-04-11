# AFML: pp 142 - 145

##### 10.3 Bet Sizing From Predicted Probabilities

- $p[x]$: x 发生的概率，$x\in\{-1,1\}$
- Null hypothesis $H_0$: $p[x=1]=1/2$
    - $z=\frac{p(x=1)-1/2}{\sqrt{p(x=1)p(x=0)}}\sim \mathcal{N}(0,1)$
- 设置 bet size 为 $2\Phi(z)-1$，其中$\Phi$是CDF of standard normal distribution

对于多余两个outcome的，

- 假设$Y=\{-1,\cdots,0,\cdots,1\}$是label，我们估计每一个label的probability $p_i$, 且$\sum_{i=1}^{|X|}p_i=1$.

- $\tilde{p}=\max_{i}p_i$ 选择 标签 $Y[i] =\arg\max_i p_i$. 
- Null hypothesis $H_0$: $\tilde{p}=1/|Y|$
    - $z=\frac{\tilde{p}-1/|Y|}{\sqrt{\tilde{p}(1-\tilde{p})}}$, $z\in(0,\infty)$
- 设置bet size为 $m=y(2\Phi(z)-1)$, $m\in(-1,1)$, $\Phi(z)$ regulates the size for a prediction $y$。

##### 10.4 Averaging Active Bets

- 每一个bet都随带一个holding period，从它originated到遇到一个barrier
- 不好的做法：重下一个old bet as a new bet arrives => excessive turnover 交易trigger过多
- 表较好的做法是，average all sizes across all bets still active at a given point in time

##### 10.5 Size Discretization

- 离散化bet size: $m^*=\text{round}(\frac{m}{d}) d$
- 减少小单
