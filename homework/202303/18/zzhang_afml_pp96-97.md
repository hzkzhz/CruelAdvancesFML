# AFML: pp 96-97

##### 6.3.2 Improved Accuracy

- majory voting
- 总共有N个sample，k个class，预测对的condition就是$X > N/k$
    - $P[X > N/k]=1-P[X \le N/k]=1-\sum_{i=0}^{N/k}\binom N i p^i(1-p)^{N-i}$
    - p就是预测对的概率。如果N足够大，$N > p/(p-1/k)^{2}$ ，则$p>1/k$ 也就是$P[X>N/k]>p$，bagging的效果会更好。

##### 6.3.3 Observation Redundancy

冗余observation对有bagging有两个不利影响。

1. 替换抽取的样本更有可能几乎完全相同
    - 解决方案：1）限制sample数量；2）用 sequential bootstrap
2. out-of-bag会被高估
    - 用stratified k-fold CV，而且n_split小一点比较好。
        - 如果n_split过高，test set跟training set会过于相似

