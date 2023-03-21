# notes
作者介绍了 fixed width window fracdiff，完全没看懂这是什么操作。总之这就解决了 negative drift 的问题。最终的结果不再是正态的，但是是 stationary 的。根据图依然没有理解什么是 negative drifting。

然后作者讲解了stationarity with max memory preservation。那么我们知道这个 d 越大越 stationary，同时存储的信息也就越少。所以我们希望找到最小的 d 使得这个得到的序列依然是 stationary，此时则保留了最多的信息。

后面实在是没看懂，放弃了。看看 modelling 在讲啥。


根据斯特林公式，我们有：
$$
\lim_{n->\infty} \frac{n!}{\sqrt{2\pi
n}(\frac{n}{e})^n}  = 1
$$

根据极限的定义，我们得到：对于任意 $\epsilon$ 我们都能找到一个 $N$ 使得任意 n > N 都有：
$$
1 - \epsilon < \frac{n!}{\sqrt{2\pi
n}(\frac{n}{e})^n} < 1 + \epsilon
$$

对上式取对数后可以得到：

$$

\log(1 - \epsilon) < \log(n!) - C_1 n\log n < log(1 + \epsilon)

, \;\;\;n > N
$$

这里 $C1$ 就是计算得到的一个常数，具体是多少并不重要不用算出来。

我们随便取一个 $\epsilon < 1$ ，然后调整这个系数。

我们把 C1 调整大一点就可以让上面这个式子右边小于 0，进而说明 log(n!) = O(nlogn)。

我们把 C1 调整的小一点就可以让上面式子左边大于 0，进而说明 log(n!) = \Omega(nlogn)。

具体的调整方法为：

调整大一点：
令 $C_2 = C_1 + \frac{\log(1+\epsilon)}{N\log N}$

调整小一点：
令 $C_3 = C_1 - \frac{|\log(1+\epsilon)
|}{N \log N}$



