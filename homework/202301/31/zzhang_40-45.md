# AFML: pp 40 - 45

3.2 Fixed-time horizon method

- $y_i\in\{-1,0,1\}$ 表示 $t_{i,0}$ 到 $t_{i,0}+h$ 时间内的return 小于 $-\tau$, 在$[-\tau,\tau]$ 间或者大于$\tau$ ，其中$\tau$ 是hyper-parameter

缺点：

- time bar 一般没有很好的性质 => 可以用volume/dollar bar
- $\tau$ 在不同时刻应该不一样，比如开盘波动会比较剧烈 => 用之前数值weighted的 varying $\sigma$
- 没法说明比如 stop-loss相关的pattern => 还是没法解决
