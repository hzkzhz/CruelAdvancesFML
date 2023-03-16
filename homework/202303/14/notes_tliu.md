# notes

作者称：几乎所有的工作都会先把 non stationary 的序列通过 integer transformation 变换成一个 stationary 的序列。这里就会引发两个问题：

1. integer 1 differentiation 为什么是最优的？
2. 过度differentiation是不是罪魁祸首？其中罪是这些结果都非常依赖有效市场假说。

作者要开始介绍什么是 fractional differentiation 了，这是一个 computationally expensive operation 所以我们还有一些工作来高效地计算这些东西。

这里它介绍了一个 Backshift operator B，然后介绍了有关他的一些运算规则，比较浅显。就是简单的组合数。