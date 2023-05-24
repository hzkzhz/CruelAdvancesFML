# AFML: pp 249 - 251

### Ch 17. Structural Breaks

##### 17.1 Motivation

- structural breaks: 比如 transition from one market regime to another
- 例如，均值回归模式可能让位于动量模式。 随着这种转变的发生，大多数市场参与者都措手不及，主要靠别人的错误获利
- 本章主要测量了structural breaks的可能性的方法。



##### 17.2 Types of Structural Break tests

两类：

1. CUSUM tests: 测试cumulative forecasting erros是否显著地偏离white noise
2. Explosiveness tests: 除了偏离white noise，测试process是否表现出指数增长(exponential growth) 或崩溃 (collapse)，因为这与随机游走或平稳过程不一致，并且从长远来看是不可持续的
3. Right-tail unit-root tests: 假设自回归的时候，测试是否有指数增长或崩溃
4. Sub/super-martingale tests: 测试评估各种函数形式下是否存在指数增长或崩溃



##### 17.3.1 Brown-Durbin-Evans CUSUM Test on Recursive Residuals

- 矩阵$X_t$由特征$t\le T$的时间序列组成，$\{x_i\}_{i=1,...,t}$。

- 用 recursive least squares (RLS) estimates of $\beta$:

    - $$y_t = \beta_t'x_t+\epsilon_t$$

    - 用 subsamples [1, k+1], [1, k+2], ..., [1, T] 来预测得到 $\hat{\beta}_{k+1}$, ..., $\hat{\beta}_T$.
    - recursive residual: $\hat{w}_t=\frac{y_t-\hat{\beta}_{t-1}'x_t}{\sqrt{f_t}}$ 
        - $f_t=\hat{\sigma}_{\epsilon}^2[1+x_t'(X_t'X_t)^{-1}x_t]$
    - CUSUM statistic 是 $S_t = \sum_{j=k+1}^t \frac{\hat{w}_j}{\hat{\sigma}_w}$
        - $\hat{\sigma}_w^2 = \frac{1}{T-k}\sum_{t=k}^T (\hat{w}_t - E[\hat{w}_t]^2)$

- 零假设：$\beta_t=\beta$ (constant), $S_t\sim N[0, t-k-1]$

- 缺点：初始点事随便选的，所以结果可能不稳定



##### 17.3.2 Chu-Stinchcombe-White CUSUM Test on Levels

- 零假设改成：$\beta_t = 0$ 也就是没有变化：$E_{t-1}[\Delta y_t] = 0$
- standardized departure of log-price $y_t$ relative to loh-price at $y_n$, t> n:
    - $S_{n,t}=(y_t - y_n)(\hat{\sigma}_t\sqrt{t-n})^{-1}$
    - $\hat{\sigma}_t^2 = (t-1)^{-1} \sum_{i=2}^t (\Delta y_i)^2$
- 零假设 $H_0$：$\beta_t = 0$, 则$S_{n,t}\sim N[0,1]$
- 则 time-dependent critical value ofr the one-sided test is 
    - $c_{\alpha}[n, t]=\sqrt{b_{\alpha}+\log [t-n]}$
- 缺点：reference level $y_n$ 比较随意，可以用backward-shifting window $n\in[1,t]$ 来估计 $S_{n,t}$ 然后选择 $S_t=\sup_{n\in[1,t]} \{S_{n,t}\}$

