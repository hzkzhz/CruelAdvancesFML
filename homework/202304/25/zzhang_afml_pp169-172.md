# AFML: pp 169-172

### Ch 13 Backtesting on Synthetic Data

##### 13.1 Motivation

- 用历史数据生成synthetic dataset做回测

##### 13.2 Trading Rules

- 投资策略可以定义为假定市场无效率存在的算法
    - 依靠计量统计学模型、宏观经济变量，基本面、accounting information

- 每个investment strategy 都需要一个implementation tactic，通常称为 trading rules
- 虽然strategies在本质上可能非常多样化，但tactics却相对同质
    - trading rules提供了进入和退出头寸必须遵循的算法（比如策略信号达到特定值时建仓，达到thresholds for profit-taking and stop-losses的时候平仓）
    - 依赖由历史模拟calibrated的参数 => 可能会导致backtest overfitting
- 我们对如何退出感兴趣（头寸已经在了，如何以最佳方式退出）

- 虽然可以确定extent of overfitting然后抛弃一些策略，但最好还是从一开始就减少trading rule calibration的overfitting。
    - 可以直接从生成数据的随机过程中得到最优的参数，而不是historical simulations
    - 可以从historical sample中characterize生成所得observation的随机过程，然后推导出optimal parameter

##### 13.3 The Problem

- 投资策略$S$ 投资 $i=1,\cdots,I$ 机会，每个机会 $i$，投资$m_i$ 个unit的$X$，其中进入这个机会的价格为$m_iP_{i,0}$，其中$P_{i,0}$ 是交易$m_i$ 个X的平均价格。由于其他人也会交易$X$，所以我们可以按市值计价(market-to-market, MtM)观察t个交易之后的交易价格$m_iP_{i,t}$。我们还可以计算 t 次交易之后的MtM pnl: $\pi_{i,t}=m_i(P_{i,t}-P_{i,0})$
- trading rule: 如何退出机会 $i$: at $t=T_i$
    - $\pi_{i,T_i}\ge \bar{\pi}$: $\bar{\pi}>0$: profit-taking threshold
    - $\pi_{i,T_i}\le \underline{\pi}$: $\underline{\pi} < 0$: stop-loss threshold
    - 相当于horizontal barriers
    - trading rule就是设置这两个threshold $R:=\{\underline{\pi}, \bar{\pi}\}$
- 如何选择合适的$R:=\{\underline{\pi}, \bar{\pi}\}$？ 在一个set $\Omega:=\{R\}$ 里试到一个optimal的
- Overfit的评判标准：IS里最优的$R^*$ 的sharpe ratio在OOS里比整个set里的median的要小
    - 跟第11章里介绍的PBO相同的方法去评估overfit的程度

##### 13.4 Our Framework

- 假设 discrete OU process: $P_{i,t}=(1-\varphi)E_0[P_{i,T_i}]+\varphi P_{i,t-1}+\sigma\epsilon_{i,t}$ ， $\epsilon_{i,t}\sim N(0,1)$

    - $\varphi$: $P_{i,0}$ 收敛到$E_0[P_{i,T_i}]$ 的速度

- 上面的式子意味着 performance of opportunity $i$: 

    $$\frac{1}{m_i}\pi_{i,t} = (1-\varphi)E_0[P_{i,T_i}] - P_{i,0}+\varphi P_{i, t-1} + \sigma\epsilon_{i,t}$$

- 上面的OU process也保证了$\pi_{i,t}$服从正态分布
    - $$\pi_{i,t}\sim N[m_i((1-\varphi)E_0[P_{i,T_i}]\sum_{j=0}^{t-1}\varphi^j - P_{i,0}), m_i^2\sigma^2\sum_{j=0}^{t-1}\varphi^{2j}]$$
    - 给定 $\sigma, \varphi$ 就给得到 最优的$R^*:=\{\underline{\pi}, \bar{\pi}\}$

