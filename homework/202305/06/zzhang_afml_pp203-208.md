# AFML: pp 203-208

##### 14.7 Efficiency

- risks involved in achieving those results (profits, losses, and costs)

##### 14.7.1 The Sharpe Ratio

- 如果return是iid $N(\mu,\sigma^2)$ 分布的，sharpe ratio = $\mu/\sigma$
- 但是真实的$\mu$ 和$\sigma$没法知道，所以有很高的estimation error

##### 14.7.2 The Probabilistic Sharpe Ratio

- PSR 去除了消除由具有skew和/或fat-tailed的短期序列引起的inflation效应。.
- 给定benchmark $SR^*$ 和 observed $\hat{SR}$，我们计算 $\hat{SR} > SR^*$ 的概率
- $$\hat{PSR}[SR^*]=Z[\frac{(\hat{SR}-SR^*)\sqrt{T-1}}{\sqrt{1-\hat{\gamma}_3\hat{SR}+\frac{\hat{\gamma}_4-1}{4} \hat{SR}^2}}]$$
    - $\hat{\gamma}_3$ 是 skewness of the returns
    - $\hat{\gamma}_4$ 是 kurtosis of the returns
    - $\hat{PSR}$ 增大如果
        - $\hat{SR}$ 增大
        - 更长的track record T
        - 正的skewed return
        - 更thin 的tail => $\gamma_4$ 减小

##### 14.7.3 The Deflated Sharpe Ratio

- DSR：调整拒绝阈值以反映试验的多样性的PSR
- $SR^*$ 不再是用户给的了，而是
- $SR^*=\sqrt{V[\{\hat{SR}_n\}]}(1-\gamma)Z^{-1}[1-\frac{1}{N}]+\gamma Z^{-1}[1-\frac{1}{N}e^{-1}]$
    - V[.]是序列的variance，N是独立实验的数量，$\gamma$ 是Euler-Mascheroni constant
- 理由就是：试验的次数足够多总有一个好的，所以benchmark会随着你试验的variance增大，也会随着你尝试的trails数增大
- backtesting的第三条law：每次backtest都应该随着报告试验的所有trail，不然很有可能是false discovery

##### 14.7.4 Efficiency Statistics

- Annualized Sharpe ratio：*假设了return是IID的*，按照参数$\sqrt{a}$年化，$a$ 是每年平均观察到的return个数
- Information ratio：和benchmark对比。excess return, tracking error
- Probabilistic Sharpe ratio：前面介绍了
- Deflated Sharpe ratio：前面介绍了
    - 针对由non-Normal returns、track record length和multiple testing/selection bias引起的inflation校正 SR。 对于 5% 的标准显着性水平，它应该超过 0.95。 它可以根据绝对或相对回报来计算。

##### 14.8 Classification Scores

- 主算法identify机会，次算法决定是否抓住机会还是pass
- 分类的metric：Accuracy，Precision，Recall，F1
- 如果分类的类别unbalanced：positive 和negative的分开算F1，Negative log-loss

##### 14.9 Attribution

- decompose the PnL in terms of risk classes
    - 比如一个公司债PM就会想知道收益是从哪些risk来的，比如duration，credit，liquidity，economic sector，currency，sovereign，issuer等等，这些risk之间correlation其实还挺高
    - 可以计算每个risk class的Sharpe ratio/information ratio
    - 最有名的就是Barra's multi-factor method
- PnL归因五步：
    - 第一步，确保 *investment universe* 内的每个成员在任何时间点都属于每个风险类别的一个且仅属于一个类别。 换句话说，对于每个风险类别，我们将整个投资领域分成不相交的分区
    - 第二步，对于每个风险类别，我们为每个风险类别形成一个指数。 例如，我们将计算一个短期债券指数、另一个中期债券指数和另一个长期债券指数的表现。 每个指数的权重是我们 *portfolio* 的重新调整权重，因此每个指数的权重加起来为 1。
    - 第三步，重复第二步，但这次我们使用*investment universe*的权重（例如 Markit iBoxx 投资等级）形成这些风险类别指数，再次重新调整，使每个指数的权重加起来为 1
    - 第四步，计算关于这些指数的回报和超额回报的绩效指标。 为清楚起见，在此上下文中，短期指数的超额回报是使用（重新调整）*portfolio weightings*（步骤 2）的回报减去使用（重新调整）*universe weightings*（步骤 3）的回报。
