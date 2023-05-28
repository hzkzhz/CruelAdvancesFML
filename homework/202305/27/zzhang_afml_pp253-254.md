# AFML: pp 253 - 254

##### 17.4.2.1 Raw vs Log Prices

- 在有bubble 和 burst的时候 log price 会更好
- return的volatility当价格升高的时候会减小，当价格降的时候升高 => 为了保持price的constant variance
    - 在 raw price上做ADF，return的variance必然不和price level invariant，不然就异方差了
- 如果用log price 则ADF有 $\Delta \log y_t\propto \log y_{t-1}$，如果有好几倍的价格（bubble）$x_t=ky_t$ 则 $\log x_t = \log k + \log y_t$ 则我们依旧有 $\Delta \log x_t \propto \log x_{t-1} \propto \log y_{t-1}$.
- 价格水平决定了回报的均值，而不是回报的波动性

