##### 12.4.2 The Combinatorial Purged Cross-Validation Backtesting Algorithm

CPCV做cross-validation的方法：

1. 把T那么多的observations不shuffle地分成N组，每组T/N个
2. 计算所有可能的train/test 组合，其中N-k个组是训练集，k个组是测试集
3. purge （测试集和训练集中间要有gap）+ embargo（测试集比训练集早的话，中间需要额外的gap）
4. 在每一个训练集/测试集组合上训练（总共有$\binom{N}{N-k}$那么多组）
5. 计算$\varphi[N,k]$ backtest paths，计算每天path的Sharpe ratio，然后算 empirical distribution

##### 12.4.3 A few example

- 如果 k=1, CPCV 相当于普通CV。
- 如果 k = 2, 有 $\varphi[N,2]=N-1$ 条path，将数据分成$\varphi+1$ 组。每组中，在$\theta=1-2/T$ 的数据上训练
- 一般 k = 2 会比较好，把数据分成$N=\varphi +1 \le T$ 份。

##### 12.5 How combinatorial purged cross-validation addresses backtest overfitting

- 由于variance，既是真实的sharpe ratio是0，我们也能通过瞎试I 次找到一个strategy有Sharpe ratio为 $E[\max\{y_i\}_{i=1,\cdots,I}] = E[\max\{x_i\}_{i=1,\cdots_I}]\sigma(y_i)$，其中$y_i$ 是每个策略的Sharpe ratio，$x_i\sim N(0,1)$ 
    - 试验的次数越高，“最优策略Sharpe”的期望越高（即使真实的Sharpe是0）
- 主要是CPCV从更多的path中生成Sharpe ratio distribution
- CPCV 有更少的false discoveries than CV (cross validation) and WF (walk forward)
- path的相关性越低，CPCV的variance越低

