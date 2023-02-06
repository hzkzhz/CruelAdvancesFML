# notes

需要重新复习一下第二章。

fundamental data 需要注意具体的发布时间。只有在这个数据公之于众之后才能用这个数据。这里举了一个 Bloomberg 的例子，在它的研报中，release 日期往往在报告中包含的时间的一个半月之后。很多因子挖掘的工作在使用数据的时候，时间用的是报告里的时间，实际上我们用了一些在当时不知道的值，这在实际情况里是不存在的，所以这样的工作不实用。

fundamental data 还有一个问题是存在很多 backfilling 和 reinstated value。它们都是在第一版发布的时候不知道或者不正确的值，后来被填上或者是修正。但是关键问题是在真实使用的时候你是不能知道这些修正和填补的。

market data 包括了在交易所里发生的各种交易数据，每个交易者都会留下 footprint。存在一些算法可以分析一些交易算法或者是用图形界面的交易员的行为，推测它下一步的行动或者是估计某个交易者这个时候的交易状态之类的。
FIX（Financial Information Exchange）数据是非常大量而且相对高频的，每天都会生成大概 1TB 的数据量。所以用来做研究很有意思。

alternative 数据最有趣，最神秘。它可能是非常独家，完全没有任何处理（比如某个卫星照片，某个地方的交通情况），可能是非常及时的。但是也可能是很贵，很容易出现隐私问题的。

Remember, data that is hard to store, manipulate, and operate is always the most promising.

maybe your competitors did not try to use it for logistic reasons.