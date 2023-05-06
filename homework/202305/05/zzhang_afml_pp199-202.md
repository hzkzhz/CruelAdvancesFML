# AFML: pp 199 - 202

##### 14.5 Runs

- Runs 定义：uninterrupted sequences of returns of the same sign => 增加了downside risk

##### 14.5.1 Returns Concentration

- 给定一个return的时间序列{$r_t$}$_{t=1,\cdots,T}$ 我们可以计算两个weight list
    - $w^+_t=r_t^+/(\sum r_t^+)^{-1}$，$w^+=\{w_t^+\}_{t=1,\cdots,T}$
    - $w_t^-=r_t^-/(\sum{r_t^-})^{-1}$，$w^-=\{w_t^-\}_{t=1,\cdots,T}$
    - 也就是正的return的weight。负的return的weight。
    - 计算Herfindahl-Hirschman Index (HHI)
    - $$h^+=(\frac{E[(r_t^+)^2]}{E[r_t^+]^2-1})/(\|r^+\|-1)$$ 来计算concentration，$h^-$ 类似，越小越集中
        - $0\le h^+\le 1$
        - $h^+=0$ => uniform return
        - $h^+=1$ => 只有一个非0值
- 期望bets return有
    - high sharpe, high bets per year, high hit ratio (低负return的个数)，low h^+, low h^-, low h[t] (bets不集中在一段时间内)

##### 14.5.2 Drawdown and Time under Water

- Drawdown (DD)：两次高水位之间的最大loss

- time under water (TuW): 从一次高水位到下一次超过之前最大pnl时刻的时间

##### 14.5.3 Runs Statistics for Performance Evaluation

- 一些有用的统计量：(1) 正return的HHI ；(2) 负收益的HHI；(3) 相邻bet之间的时间的HHI；(4) 95分位的DD; (5) 95分位的TuW

##### 14.6 Impementation Shortfall

- 一些策略失败的原因是忽略了execution costs比如
    - broker fee per turnover：每笔交易要给brokerage交钱
    - Average slippage per turnover：类似每笔交易bid-ask spread

- 两个metrics

    - Dollar performance per turnover：dollar performance（包含以上两种费用）和 total portfolio turnover 的比例。

    - Return on execution costs：dollar performance（包含以上两种费用）和 total execution cost 的比例。
