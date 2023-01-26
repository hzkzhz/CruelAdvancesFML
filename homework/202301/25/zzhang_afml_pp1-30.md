# AFML: pp 1- 30

### Ch1

- difference between econometrics and financial ML
    - Econometrics 对 Financial Academia 比较有用，但实际中它太简单了
    - 如果ML发现了一个可以预测现象的feature，那可以为此创造理论

### Ch2

- bars: rows 相当于sample后每一行叫做一个bar

##### Standard Bars

- Time bars: 按设定的interval去sample。
    - 在low-activity的时期oversample了，在high-activity的时期under sample了
    - 有很多SC、异方差、non-normality of return的问题
- Tick bars:  按设定的tick去sample。
    - 按tick来sample，return差不多是IID Gaussian
    - 需要注意auction trade （open和close的时候，一个tick里其实包含了非常多match）
    - 但10 lots拆成10个单去下，是10个tick；一个单去下，是1个tick
- Volume Bars: 按设定的volume去sample
    - return: 比tick bars的方法更 closer to IID Gaussian
- Dollar Bars: 按设定的改变的value 去sample
    - 适合有剧烈price fluctuation的时候
    - 每天bars的数量比较稳定（相volume, tick等)
    - 考虑了拆/合股、发新股/回购带来的price变动的问题

##### Information Bars

1. Tick Imbalance bars (TIB)

    - $b_t=1$ 如果上涨，$b_t=-1$ 如果下跌，保持的话就和$b_{t-1}$一样，$t$ 表示一个tick
    - $\theta_T=\sum_{t=1}^Tb_t$ 表示累计的signed ticks

    - $$T^* =\arg\min_T\{\|\theta_T\|\ge \mathbb{E}_0[T]*\|2\mathbb{P}[b_t=1]-1\|\}$$
    - 超过threshold 就构成一个bar。其中 $\mathbb{E}_0[T]$ 和 $\|2\mathbb{P}[b_t=1]-1\|$ 都是期望值，可以从之前的bars里算

2. Volume/Dollar Imbalance bars (VIB, DIB)

    - $v_t$ 表示 t 这个tick的volume或者dollar
    - $\theta_T=\sum_{t=1}^Tb_tv_t$ 注意每个tick $b_tv_t$ 有正有负
    - $v^+=\mathbb{P}[b_t=1]\mathbb{E}_0[v_t|b_t=1]$ 上涨的时候期望volume
    -  $$T^* =\arg\min_T\{\|\theta_T\|\ge \mathbb{E}_0[T]*\|2v^+-\mathbb{E}_0[v_t]\|\}$$

