# notes

这里又有三个看不懂的点：

rebalance costs
bid-ask spread
volume

这三个值是我们的策略额外需要的三个值。rebalance cost 类似于一种负的 dividend 分红。没看懂这个公式是怎么计算的。

bid-ask spread 中文是买卖差价。不知道为什么要考虑这个。

随后的 PCA 看的也是比较迷惑。可以理解相似对角化 V 然后乘上 w 作为 weight 的系数。然后 Rn 代表的是第 n 个 component 的 risk 占比。然后我们想要的是 R 这个风险向量能够满足某个 distribution，这个时候需要计算 w。然后根据公式 w = W b，b 是目标分布，W 是给定的分解，w 是我们想要的东西。

看了半天终于看懂了。感觉省略了非常多步。