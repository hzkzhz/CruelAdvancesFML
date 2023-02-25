# notes

Bars 就是表格里面的行。

Time bars 是按照固定时间区间（或者说时间间隔）采样得到的信息。比如可能是每分钟采样一次。里面的信息包括时间戳，平均价格，这个区间里开始的价格，结束的价格，最高价最低价，交易量等。

按照固定的时间间隔来采样其实是比较有问题的。因为人类很喜欢在早上开盘的时候进行一些交易，晚上快收盘的时候不太会有大量交易。随着交易市场中算法和机器的比例增加，CPU 时钟周期的相关性大大增加。而且这样采样得到的信息性质也比较差。

tick bars 是按照固定数量 tick 区间采样得到的信息。比如每 100 个 tick 采样得到的信息。这样采样得到的信息容易有更好的性质. price 在 tick 区间上的变化遵循高斯分布，在时间区间上的变量可能遵循帕累托分布，方差是无穷。

IID Gaussian 过程是 independent indentical distribution 独立同高斯分布过程。

tick bars 需要注意集合竞价，比如上交所开盘十几分钟的时候并不是连续竞价，挂的单会在最后的时候统一清掉。这个时候可能会生成一个 tick，但是其实本质上可能是上千个 tick。