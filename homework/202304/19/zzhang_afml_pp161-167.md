# AFML: pp 161 - 167

### Ch 12 Backtesting through Cross-Validation

##### 12.1 Motivation

back-test的两种方式

- Walk-forward: 模拟过去
- 模拟场景（不一定过去真的发生过）

##### 12.2 The walk-forward method

好处：

- 有historical interpretation 能够解释
- 确保testing set是out-of-sample（只要实现得没问题）

坏处：

- single scenario
- WF好不代表future performance好，很可能overfit了
    - 改变observation的顺序，outcome就不稳定
    - 比如从07的数据一直跑到17和从17的数据backward跑到07，结果就差别很大
- 大部分信息只被很少的决策用到，如果延长warm-up的时间，则可用来backtest的数据量就大大减少了。假设一个策略用了 $[0,t_0]$的数据（总共$T$那么多数据），则一半的decision $\frac{T-t_0}{2}$ 平均只用了 $\frac{1}{4}T+\frac{3}{4}t_0$ 那么多observation。

##### 12.3 The cross-validation method

- 如何模拟stress scenario （比如2008）

- 用cross-validation => simulate the performance of a classifier that knew everything except for that period.
    - 好处：相同的时间span，所以表现comparable；有K个场景；没有warm-up，所以能回测的数据多
    - 坏处：single path；没什么historical interpretation；可能有leakage

##### 12.4 The combinatorial purged cross-validation method (CPCV)

- 给定$\varphi$ 为# targeted backtest paths，CPCV输出需要的训练集/测试集组合。



##### 12.5 How combinatorial purged cross-validation addresses backtest overfitting



