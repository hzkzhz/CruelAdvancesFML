# AFML: pp 81-83

5.5.1 Expanding window

- negative drift => 是由window expand的时候加在初始observation的负权重导致的

- 控制weight loss之后，negative drift缓和很多，但还是很大
    - 用fixed-width window

5.5.2 Fixed-width window fracdiff

- window size 有上限 （$|w_{l^*}|\ge \tau$ 的部分才保留），超过的部分，weight都是0
- $l^*$ 之后的window，weight vector都是相同的
- 好处：没有了negative drift，是个stationary的序列（但 skew + excess kurtosis）

