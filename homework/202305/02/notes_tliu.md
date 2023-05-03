# notes

学习了 KL散度的 argmin和cross entropy 的 argmin 是一样的，这给我们使用 cross entropy 作为 loss function 提供了理论依据。

更具体的：H(p, q) = H(p) + D_KL(P||Q) 也就是说交叉熵就是 p 的熵加上 PQ 的 KL 散度。

网上搜索 cross entropy 全都是 ML内容，wiki 上有原汁原味的关于信息论的部分：

In information theory, the cross-entropy between two probability distributions 
�
p and 
�
q over the same underlying set of events measures the average number of bits needed to identify an event drawn from the set if a coding scheme used for the set is optimized for an estimated probability distribution 
�
q, rather than the true distribution 
�
p

也就是说交叉熵可以用来衡量：如果我们用 q （推测的分布）优化的编码中 draw 一个 event，我们需要多少个 bit 才能判断这到底是哪个事件，如果 p 才是真实分布的话。