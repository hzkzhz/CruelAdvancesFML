# AFML: p88

小结：

大多数经济相关序列有两个现象：

1. Box-Jenkins: Return序列是stationary但memory-less
2. Engle-Granger：log-price 有memory 但 non-stationary。可以利用cointegration。但是cointegrated variables有限制且cointegrating vectors经常不稳定

本章节介绍的FFD方法可以既让序列stationary又不把memory全去掉了。

推荐transform feature的步骤：

1. 计算cumulative sum，保证了还是需要一些differentiation的
2. 计算FFD(d) series，$d\in[0,1]$
3. 决定最小的 d 让 ADF stats of FFD(d) 显著
4. 用FFD(d) series。
