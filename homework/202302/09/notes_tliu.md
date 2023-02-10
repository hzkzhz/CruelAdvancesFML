# notes

tick bars 的一个问题在于：order fragmentation 会引入一些 arbitrariness in the number of ticks。就是说如果我一笔单子是 10手，和我十笔连续的单子分别是1手，在 tick bars 意义下，就是很不一样的，但是本质上是没区别的，可能都是一瞬间发生的。除此之外，交易所的撮合算法也可能会把一笔单子分拆成几笔，为了操作上方便。

volume bars 可以避免这个问题，它每次选择的是固定的交易量区间，比如每1000手作为一个bar。

在 1960s，vendors 基本上不提供 volume data，大家都比较关心 tick 数据。

dollar bars 也有其意义。虽然我们直觉上看，股票的价格是会变化的，所以按照 dollar 来算不是很有道理，如果股票翻倍或者是腰斩，这个都会变的非常多。但是我们考虑到大家钱的量一般是固定的，愿意投入的钱也是差不多的，所以反而是 volume 在价格比较波动的时候会有比较大的问题。