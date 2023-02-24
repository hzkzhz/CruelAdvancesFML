# notes

single future roll 完全看不懂，很多术语不知道是什么意思。看起来应该先找一个金融英文书简单入门一下。

假装这部分看懂了，接下来是 sampling features。这里的意图是说我们用之前生成的数据已经可以套用 ML 算法了，但是这样的效果肯定是不好的，所以我们需要采样出一些 features matrix。

## sampling for reduction
我们想要 reduce the amount of data to fit the ML algorithm，这个过程称之为 downsampling。有两种简单的方法：linspace sampling / uniform sampling。linspace sampling 就是非常简单的隔一段距离就采样一下，最简单的方式。
uniform sampling 就是采样的点是均匀分布的到的。

这两个采样都操作简单，但是可能会丢失一些重要的信息。

## event based sampling
金融市场上可以出现一些大事件 event，我们可以学习 whether there is an accurate prediction function under those circumstances

CUSUM filter 是一种 event based sampling method。简单来说就是每次把观测到的值和对它的期望做个差，然后每次把这个差加起来。检测这个差的和，如果大于一个 threshold 就 alert。