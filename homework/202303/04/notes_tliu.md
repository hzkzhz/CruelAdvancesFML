# notes

这里介绍了一下 confusion matrix 终于看到了我能看懂的部分了。之前在入门机器学习的时候就学过一遍这次再来一遍。

首先英文里我们把预测分为四种：

TP，TN，FP，FN

T 和 F 代表这次预测的是不是对的
P 和 N 代表这次预测的结果是什么

所以 FP 代表这次预测的结果是 positive 但是这是错误的，所以真正的结果是 negative。

precision 代表的是 TP / (TP + FP)。所以 precision 高说明如果预测是 P 的话很可能真的是 P。

recall 代表的是 TP / (TP + FN)。所以 recall 高代表的是我把尽可能多的 postive 挑出来了。

accuracy 代表的是 (TP + TN) / (TP + TN + FP + FN)，所以 accuracy 高相对来说比较综合。

F1 分数就是它们的调和平均值。

然后作者吹嘘了一下为什么 meta labeling 比较牛逼，没有太看懂。感觉还是玄学。大概意思就是把 side 和 size 这两种东西分离开来。