# AFML: pp 152-157

##### 11.3 Even if your bacttest is flawless, it is probably wrong

- 在对同一数据集运行多个测试后不可避免地出现的统计侥幸。
- 其实就是说95%的confidence是significant的，那测100次，预期有5次在不significant的情况下把它错误归为significant了

##### 11.4 Backtesting is not a research tool

- 即使有些特征很重要，也不代表可以通过投资策略变现；相反，有很多策略看起来是有利可图的，即使它们是基于不相关的特征
- 特征重要性是一个真正的研究工具，因为它可以帮助我们了解 ML 算法发现的数据pattern
- 回测不是研究工具，它无法使我们深入了解特定策略为何会赚钱
- 回测的目的是丢弃不良模型，而不是改进它们。根据回测结果调整模型是浪费时间且很危险
- 投入时间和精力，让所有组件都正确无误而不是靠回测去改：structured data, labeling, weighting, ensembles, cross- validation, feature importance, bet sizing。
- 在您的模型完全指定之前，切勿回测。 如果回测失败，则重新开始。

##### 11.5 A few general recommendations

- 由于“选择偏差”，每个经过回溯测试的策略都在某种程度上过度拟合
- 减少过度拟合的一些步骤：
    1. 为整个资产类别或投资领域而不是特定stock。投资者分散投资，所以不会只在一个stock上犯错误（因此让你有利可图），如果你只在一个stock上发现这个错误，大概率是错误发现
    2. 用bagging
    3. 在完成所有研究之前不要进行回测
    4. 记录在数据集上进行的每一次回测，以便可以根据最终选择的结果估计回测过度拟合的概率
    5. 模拟场景而不是历史。历史只是实现的随机路径，它可能完全不同。
    6. 如果回测未能确定有利可图的策略，请从头开始， 抵制重复使用这些结果的诱惑。

##### 11.6 Strategy selection

- 在time series的数据集上做cross validation要考虑serial conditionality in labels
- scikit-learn有walk-forward timefold method，测试向前移动以防止leakage，和历史回测差不多。但是如果有long-range serial dependence，一个远离end of training set的测试也可能会有leakage。
- walk-forward还容易overfit，因为只有一条测试路径

 ######  基于回测过拟合（PBO）概率估计的用于策略选择的 CV 方法

- 用 组合对称交叉验证 (CSCV) 方法 估计 PBO

    1. 根据 $N$ 个trails构造matrix $M\in R^{T\times N}$, 每列 表示第 n 个模型在 1-T时间内的PnL。用于选择“最佳”策略的性能评估指标可以在每列的子样本上进行估计

    2. 把矩阵横着切成偶数S份，$R^{(T/S)\times N}$

    3. 构造所有组合（每组$S/2$个小矩阵）$C_S$，共有$\binom{S}{S/2}$ 个

    4. 对于每个组合$c\in C_S$: 

        - 用组合里那$S/2$个小矩阵构造一个训练集 $J$ ，所以训练集的时间跨度是T/2（不要求连续）；测试集就是另一半矩阵
        - 用$R$ 来表示训练集里每个model的performance，来计算并决定最好的model $n^*$；用$\bar{R}$ 表示测试集里每个model的performance
        - 计算$\bar{R}_{n^*}$ 在 $\bar{R}$ 里的rank，也就是训练集里最好的模型在测试集里的表现rank，$\bar{\omega}_c\in(0,1)$ ，如果没有overfit，那 $n^*$在测试集里的表现也应该最好。越靠近1说明表现越好。
        - 定义 logit $\lambda_c=\log[\frac{\bar{\omega}_c}{1-\bar{\omega}_c}]$ 如果 $\lambda_c=0$ 则表示 $n^*$ 是median。$\lambda_c$ 越小（负的）表示可能overfit了。

    5. 对每个组合$c\in C $ 计算$\lambda_c$ 。用$f(\lambda)$ 比表示relative frequency

        at which $\lambda$ occurred across all $C_S$ 相当于概率密度，然后用$\int_{-\infty}^0f(\lambda)d\lambda$ 来估计PBO。

- 这个方法的好处：每个子集中的观察结果保留了原始时间序列。 随机抽样是在相对不相关的子集上进行的，而不是在观察上进行的。
