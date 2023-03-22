# notes

ML 模型的错误往往来自这三个原因：

bias variance noise

上一节我们讲解了 bias 和 variance，来源是维基百科和 sklearn的官网。

作者这里也解释了 bias 的来源。他认为 bias 来自于 unrealistic assumptions。当 bias 比较高的时候 ML 算法没办法识别重要的特征和输出之间的关系，叫 underfit。

variance 来自于对训练集微小变化过度敏感。

noise 是训练数据本身的 variance。我们理论上来说训练数据应该是准确无误的，但是实际上并不是如此，本身就有一个方差。这是没办法解决的问题。

然后作者给了一个很容易推导的公式，说明了：

预测值与真实值的差的方差 = bias^2 + variance + noise。这个公式形式化的解释了到底什么是 bias 什么是 variance，什么是 noise，点赞。