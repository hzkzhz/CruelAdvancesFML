# AFML: pp 75-76

## Ch 5: Fractionally Differentiated Features

5.1 Motivation

- 金融series: 低信噪比 => standard stationary transformations（如整数微分）通过移除内存进一步减少该信号。
- 价格序列具有记忆性，因为每个值都依赖于之前一段时间的价格走势；但是integer differentiated series，比如return，有memory cut-off的负面影响，用几个sample window后很容易把history给忽视了

- 主要介绍data transformation method that ensures the stationarity of the data while preserving as much memory as possible.

5.2 The stationary vs. memory dilemma

- series 的non-stationary主要就是由 memory导致的
- 一般序列分析会希望series是stationary的，但是通过一些手段让它stationary之后，把memory也去掉了；memory才是模型拥有预测能力的关键
- Return是stationary但memory-less的；Price由memory但是non-stationary
    - 想要*stationary series where not all memory is erased.*
    - Cointegration 协整 => model series with memory
- 监督学习需要stationary feature
- 总的来说trade-off就在于，differentiation能让序列stationary但是会消除memory。

5.3 Literature review

- （1）为什么整数一阶差分（比如计算log return）是最优的？（2）多阶差分是不是学术界那么强调有效市场假说的原因？
- fractional differencing （差分的degree是分数）的ARIMA比标准的ARIMA表现好
    - 分数差分提供了long-term persis- tence and antipersistence

