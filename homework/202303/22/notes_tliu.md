# notes

首先我们需要补全什么是 ensemble method。这个作者默认大家已经会了，我们先去 scikitlearn 官网上学习一下。

ensemble 直接翻译是马戏团乐团的意思，也可以是“一起出现”，“合奏”的意思，显然现在是后者。

它的意思是就是我们有若干个 estimator，然后我们根据这若干个 estimator 建造一个新的 estimator。比如说最简单的方案就是把所有的 estimator 的输出结果取一个平均值，这样的话我们的方差就会被极大地缩小（比如现在有 n 个输出结果独立同分布的 estimator，显然我们使用这个平均值更优因为平均值不变方差减小）

我们一般都听说过 boost method 把若干个比较弱的 predictor 拼凑出一个比较强的 predictor，它的方法是按照顺序训练分类器，每个分类器都尝试去修正之前的 combined estimaotr 的 bias。

同时作者还推荐去看 wikipedia 上的一个页面 bias and variance


bias 就像是你的模型的期望和真实值之间的距离；variance 就像是你的模型的方差，很大的话就像是打耙的时候天女散花一样

在训练模型上，bias 高的模型意味着很可能模型并没有学到数据的精髓，可能会出现 underfitting；variance 高的模型可能对噪声比较敏感

wiki 举了一个非常好的例子讲述模型的参数多少（也就是大家常规意义下对模型复杂程度的定义）和 variance 并没有直接联系。比如 fab(x) = a sin(bx) 这个函数可以拟合任意数列，只要震荡的够快。

剩下的统计公式看起来就看不懂，下次一定