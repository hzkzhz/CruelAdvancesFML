# notes

作者在这里抨击了一下 sklearn 中的  cross validation 的实现。

其中有两个bug：得分函数并不知道 classes_，这是因为 sklearn 依赖numpy array，而不是 pandas series。

另外一个 bug 是 cross val score 得到的结果并不是 log loss 结果。

这两个都没看懂是什么意思。 第一个issue我去github上看了一下，发现时至今日，依然没有解决。居然这么可怕。

来到下一章 feature importance。
作者认为在同一个 test data 上不停的跑，最终大概率会得到一个虚假的发现。为了解决这样的问题，作者提出了一个我看不懂的词叫 feature importance。