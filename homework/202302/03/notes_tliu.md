# notes

fixed-time horizon method 基本所有的 ML 算法都在用（指金融相关）。

这个方法会生成这样的标签：

$$
yi = -1 \; if \; r_{t_{i,0}, t_{i,0}+h} < -\tau \\
   = 0 \; if \; |r_{t_{i,0}, t_{i,0}+h}| < \tau \\
   = 1 \; if \; r_{t_{i,0}, t_{i,0}+h} > \tau \\
$$

其中 r 是 price return，

$$
r_{a, b} = \frac{p_b}{p_a} - 1
$$

不过按照一个固定的常数 threshold 是有很多弊端的。这个阈值可以是一个动态的，比如用（类似滑动窗口）rolling exponentially weighted standard deviation of returns 也就是用实时指数权重回报标准差来作为阈值。或者是我们不用 time bars 改用 dollar bars 或合适 volume bars，它们的波动不会很大基本上就是常数。

homoscedasticity 同方差性
