# notes

学习了一个新东西叫 k fold cross validation

每次我们把数据集分成 k 组，然后挑一组作为我们的验证集。

执行这样的操作直到每一组都当过验证集。最后我们的评价指标是 k 个验证集的平均值

但是这样的操作在 finance 上并不是很好用，原因是 observation 并不是 IID 的，也就是说之前的观察会影响到后面的观察。

所以理论上我们应该消除 train 和 validation 之间的 correlation，不然的话模型学到的可能并不是预测的能力而是从 correlation 中学到了过拟合的错误信息。

这里的解决方法是可以剔除相邻的值，这样缺少了关键的信息，时间上不再是相邻的，这样也就可以降低correlation。