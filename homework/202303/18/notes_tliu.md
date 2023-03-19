# notes

前面我们已经说明了 fractional differentiation 的公式，然后非常简单的证明了它的收敛性，进而说明了这个时间序列是 stationary 的。

现在我们来看 implementation 。

作者又要介绍黑科技了，有两种方法，一种是非常传统的 standard expanding window，听起来就非常有改进的空间。另一种是作者自己起的名字：fixed width window fracdiff。

对于一个有限长度的序列来说，计算的时候第一个点的差分值所蕴含的信息是比最后一个点的差分值蕴含的信息多的。这是因为第一个点用到的值是整个序列，但是后面的值用的是后面的部分，前面的部分就少掉了。所以我们这里需要计算一个 weight loss，用来衡量总共有多少 weight 少掉了。

如果我们发现一个点 weight 已经少掉了很多，我们就把它要剔除。这个点具体在什么地方和 wk 这个序列的收敛速度有关。

如果不控制 weight loss，就会出现 negative shifting，并没有看懂这是什么东西。作者提出的 fixed window fracdiff 就可以解决这个问题。