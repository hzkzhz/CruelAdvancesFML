# notes

information driven bars 没有看懂那一段是在说什么。大概意思是说可能会出现一个 imbalanced 的情况，这个时候需要一个 information driven sampling 来应对一些 informed trader。

## tick imbalance bars

我们根据tick的价格序列构造一个新的序列 b，b 代表的是价格变化是正还是负，正就是1，负就是-1.

简称为 TIBs

TIBs 采样的目的是每当 tick imbalance 超过我们的预期的时候就去采样一下。这里的tick imbalance根据上下文来看就是指tick价格大幅度变高或者是大幅度减小。可能这里就是有人埋伏或者是有人提前知道了某些信息知道会爬升到这个高度，或者是某个人要影响市场价格之类的。

然后我们定义了一个 T*-contiguous 的概念，说的是 最小的T使得imbalance超过了我们的预期。