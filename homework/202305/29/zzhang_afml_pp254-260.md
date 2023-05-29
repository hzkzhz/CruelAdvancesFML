# AFML: pp 254 - 260

##### 17.4.2.2 Computational Complexity

- O(n^2)

##### 17.4.2.3 Conditions for Exponential Behavior

- 改写 $\Delta \log y_t = \alpha + \beta\log y_{t-1} + \epsilon_t$ 为 $\log \tilde{y}_t=(1+\beta)\log\tilde{y}_{t-1}+\epsilon_t$

    - $\log \tilde{y}_t=\log y_t + \alpha/\beta$

- 因此 $\mathbb{E} \log\tilde{y}_t=(1+\beta)^t \log \tilde{y}_0$ 也就是 $\mathbb{E} \log y_t = -\frac{\alpha}{\beta} + (1+\beta)^t (\log y_0 + \frac{\alpha}{\beta})$

    - Steady: $\beta < 0: \lim_{t\to\infty}\mathbb{E} \log y_t = -\alpha /\beta$

    - Unit-root: $\beta = 0$: system is non-stationary, behave as a martingale
    - Explosive: $\beta > 0$: 负无穷或者正无穷

##### 17.4.2.4 Quantile ADF

- 用quantile来现实高ADF的集中程度
- $s_t = \{ADF_{t_0, t}\}_{t_0\in [0, t_1 - \tau]}$
- $Q_{t,q}=Q[s_t, q], q\in [0,1]$
- $\dot{Q}_{t,q,v}=Q_{t,q+v}-Q_{t,q-v}$ with $0 < v \le \min \{q, 1-q\}$

##### 17.4.2.5 Conditional ADF

- 定义 $f[x]$ 为 $s_t=\{ADF_{t_0, t}\}_{t_0\in[1,t_1-\tau]}, x\in s_t$  的概率分布。 
- ADF的集中程度 $C_{t,q}=K^{-1}\int_{Q_{t,q}}^{\infty} xf[x]dx$ 
- 高ADF的分散程度 $\dot{C}_{t,q}=\sqrt{K^{-1}\int_{Q_{t,q}}^\infty (x-C_{t,q})^2f[x]dx}$ 
- K 是 regularization constant，$K=\int_{Q_{t,q}}^\infty f[x]dx$
- outliers in s_t bias SADF_t upwards

##### 17.4.2.6 Implementation of SADF

- 略

##### 17.4.3 Sub- and Super- Martingale Tests

- Polynomial trend: $\log y_t = \alpha + \gamma t + \beta t^2 + \epsilon_t$
- Exponential trend: $y_t = \alpha e^{\beta t} + \epsilon_t$
- Power trend: $y_t = \alpha t^{\beta}+\epsilon_t$
- $SMT_t = \sup_{t_0\in [1, t-\tau]}\{\frac{|\hat{\beta}_{t_0,t}|}{\hat{\sigma}_{\beta_{t_0,t}}(t-t_0)^{\varphi}}\}$ 其中 $\varphi\in[0,1]$ 是用来penalize large sample length的。
    - 用绝对值：对 explosive 和 collapse equally 感兴趣
    - $\hat{\sigma}^2_\beta =\frac{\hat{\sigma}_\epsilon^2}{\hat{\sigma}_{xx}^2(t-t_0)}$ 所以时间长了之后 这个sigma 趋于0了。因此 SMT会对给long-term bubble 很大的值 => 需要penalize 一下long-term bubble 让它的SMT小一点。
