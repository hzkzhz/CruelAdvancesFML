# AFML: pp 281 - 286

#### Ch 19 Microstructural features

- 第一代模型：只考虑了price：有trade classification models, Roll model
- 第二代模型：考虑了volume对price的影戏那个：有 Kyle, Amihud model
- 第三代模型：PIN把bid-ask spread解释为 liquidity provider和position taker之间的一些列strategic decision。把standing order解释为option，bid-ask spread是premium。

##### 19.3 First generation: price sequences

- 通过估计bid-ask spread和volatilit来估计illiquidity

##### 19.3.1 The Tick Rule

- 按照价格变动生成一个序列：$\{b_t\}_{t=1,\cdots,T}$, 价格涨了就是1，价格跌了就是-1，不变就 = $b_{t-1}$。然后做一个分类问题
- 其他transformation：(1) Kalman filter on $E_t[b_{t+1}]$; (2) structural breaks (Ch 17), (3) entropy (Ch 18), (4) t-value from Wald-Wolfowitz runs test (知乎：如果我们算出的游程数量与预期不符，我们就可以得出结论 -- 关于这段行情是否是可预测的。); (5) fractional differentiation on the $\sum_{i=1}^t b_i$ 序列 (Ch 5)

##### 19.3.2 The Roll Model

- mid-price series: $m_t=m_{t-1}+u_t$, $\Delta m_t \sim N(0,\sigma_u^2)$
- observed price $p_t = m_t + b_tc$,  c 是bid-ask spread / 2. $b_t\in\{-1,1\}$. 
    - 假设买卖概率相同 $P[b_t=1]=P[b_t=-1]=1/2$. 前后 independent $E[b_tb_{t-1}]=0$，和noise也无关，$E[b_tu_t]=0$.
    - 可以得到 $\sigma^2[\Delta p_t]=E[(\Delta p_t)^2]-(E[\Delta p_t])^2 = 2c^2 + \sigma_u^2$, $\sigma(\Delta p_t, \Delta p_{t-1})=-c^2$. => 可以得到$c$ 和 $\sigma_u^2$ 关于$\Delta p_t$ 和 $\sigma(\Delta p_t, \Delta p_{t-1})$ 的表达式
    - 所以 bid-ask spread 是 serial covariance of price changes 的函数。
    - 真实的价格的noise 去掉 microstructural noise 是 观察到的noise和serial covariance of price changes的函数。
- 现在还会用这个模型，因为他给很少交易的securities一个effective bid-ask spread。
- 可以用这个模型生成一些有关市场liquidity的feature

##### 19.3.3 High-low volatility estimator

- 按照 High 和 Low 来估计volatility比closing price来估计好。
- $$k_1\sigma_{HL}^2=E[\frac{1}{T}\sum_{t=1}^T(\log\frac{H_t}{L_t})^2]$$
- $$k_2\sigma_{HL} = E[\frac{1}{T}\sum_{t=1}^T(\log\frac{H_t}{L_t})]$$
- 其中 $k_1=4\log(2), k_2=\sqrt{8/\pi}$
- 所以可以根据观察到的 bar 的 high 和 low来估计volatility $\sigma_{HL}$

##### 19.3.4 Corwin and Schultz

- 通过 High 和 Low 来估计 bid-ask spread
- 原则一：High 总是和offer match，Low 总是和 bid match。High-to-low price 除了反映fundamental volatility，还反映了 bid-ask spread
- 原则二：由于volatility造成high-to-low price ratio的部分会随着两个观察之间的时间差增长
- Spread, as a percentage of price：$S_t=\frac{2(e^{\alpha_t}-1)}{1+e^{\alpha_t}}$
    - $\alpha_t=\frac{\sqrt{2\beta_t}-\sqrt{\beta_t}}{3-2\sqrt{2}}-\sqrt{\frac{\gamma_t}{3-2\sqrt{2}}}$
        - $\beta_t=E[(\log\frac{H_t}{L_t})^2 + (\log\frac{H_{t-1}}{L_{t-1}})^2]$
        - $\gamma_t = [\log(\frac{H_{t-1,t}}{L_{t-1,t}})^2]$, 其中 $H_{t-1,t}$ 表示2个bar中的high
        - 建议把negative $\alpha_t$ 设置为0.
- 有一个byproduct是Beck-Parkinson volatility，在公司债市场（没有centralized order book）比较有用。
- bid-ask spread S 可以rolling window生成，生成的值可以用 Kalman filter来smooth一下。
