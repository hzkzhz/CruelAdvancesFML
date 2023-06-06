# AFML: pp 271 - 277

##### 18.7 Entropy and the generalized mean

- generalized weight: $$M_q[x, p] = (\sum_{i=1}^n p_ix_i^q)^{1/q}$$ 其中 $p_i$ 是weight，$\sum p_i = 1$ 
- geometric mean: $\lim_{q\to 0} M_q[x,p]=exp(\sum_{i=1}^n p_i \log x_i)=\prod_{i=1}^n x_i^{p_i}$
- 当 $x = \{p_i\}_{i=1,\cdots, n}$ 时，$M_q[p,p]=(\sum_{i=1}^n p_i^{q+1})^{1/q}$，定义 $N_q[p]=1/M_{q-1}[p,p]$ 
    - 对 $q < 1$，我们有 $p_i > 0, \forall i$. 
    - 如果 $p_i=1/k, k\in[1,n]$ 且 其他位置 $p_i=0$，则$N_q[p]=k$ 
    - $N_q[p]$ 给了一个描述 effective number，或者说 diversity of items
    - q 越小，给每个element更uniform的weight，给less common的element更多的weight。$\lim_{q\to0}N_q[p]$ 是非0的$p_i$ 的个数
- Shannon's entropy 是 $H[p]=\sum_{i=1}^n -p_i\log p_i = -\log[\lim_{q\to 0}M_q[p]]=\log\lim_{q\to1}N_q[p]$
- 所以相当于 Shannon's entropy 是 diversity measure的特例

##### 18.8 A few financial applications of entropy

##### 18.8.1 Market Efficiency

- 如果套利充分，则价格体现所有的信息；如果不充分则包含incomplete 信息，因此有可预测的pattern。entropy越高，重复率越低，有越多informational content. 因此，entropy of a price string可以告诉我们市场有效性的degree。decompressed market 是有效市场，因为价格信息没有重复；compressed market是非有效市场，因为价格信息有重复（entropy低）。Bubble在compressed market中形成。

##### 18.8.2 Maximum Entropy Generation

- 在未来可能的结果中，熵最大化的结果可能是最有利可图的，因为它是频率论统计模型最不可预测的结果。
- 这是最有可能触发止损的黑天鹅情景，从而产生一种反馈机制，该机制将加强和加剧走势。没太看懂

##### 18.8.3 Portfolio Concentration

- covariance $V\in R^{N\times N}$. eigenvalue decomposition: $VW=W\Lambda$
- factor loading vector: $f_\omega=W'\omega$, 其中$\omega$ 是vector of allocation，
- 每个component 产生的risk portion: $\theta_i=\frac{[f_\omega]_i^2\Lambda_{i,i}}{\sum_{n=1}^N[f_\omega]^2_n \Lambda_{n,n}}$
- Entropy-inspired definition of portfolio concentration:
    - $H = 1-\frac{1}{N}\exp(-\sum_{n=1}^N \theta_i\log\theta_i)$

##### 18.8.4 Market Microstructure

- 当 good news / bad news 的几率是even的时候，probability of informed trading可以计算为
    - $PIN = \frac{\alpha \mu}{\alpha\mu + 2\epsilon}$
    - 其中 $\mu$ 是 informed trader 的到达率， $\epsilon$ 是uninformed trader的到达率，$\alpha$ 是informational event的概率。
    - 为什么 $\epsilon$ 前面有2？
- $V_\tau^B$ , 在volume bar $\tau$ 里的买单，$V_{\tau}^S$ 是里面的卖单
- $E[|V_\tau^B - V_{\tau}^S|]\approx \alpha \mu$, $E[V_{\tau}^B + V_{\tau}^S]=\alpha\mu + 2\epsilon$ 
- 因此 我们可以计算在volume clock  $V=\alpha\mu + 2\epsilon$ 下
    - $\text{VPIN}=\frac{\alpha\mu}{\alpha\mu+2\epsilon}=\frac{\alpha\mu}{V}\approx \frac{1}{V}E[|2V_\tau^B - V|] = E[|2v_\tau^B -1|]$ 其中 $v_{\tau}^B=\frac{V_\tau^B}{V}$ 即 买单的比例
    - $2v_{\tau}^B - 1$ = $OI_\tau$ 也就是 order flow imbalance。
- 持续的订单流失衡是逆向选择的必要非充分条件。 对于做市商向informed trader提供流动性，即订单流量失衡 |OI_𝜏| 也一定是相对不可预测的。换句话说，当做市商对订单流失衡的预测准确时，他们不会被逆向选择，即使 |OI𝜏 | ≫ 0。为了确定逆向选择的概率，我们必须确定订单流失衡的不可预测性。
- 逆向选择的概率 = function of complexity of OI_𝜏
    - 给定一个volume bar的序列：每个bar的volume size是V，买单的比例是$v_\tau^B\in[0,1]$。
    - 计算 q-quantiles: $K=\{K_1,\cdots, K_q\}$ q disjoint subsets
    - Mapping: $f:v_{\tau}^B\to \{1,\cdots, q\}$
    - $X=[f[v_1^B], f[v_2^B],\cdots, f[v_N^B]]$
    - 估计entropy $H[X]$ 
    - 得到 comulative distribution function $F[H[X]]$，然后用 time series $\{F[H[X_\tau]]\}_{\tau=1,\cdots, N}$ 作为预测逆向选择预测的feature。
