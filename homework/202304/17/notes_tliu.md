# notes

作者介绍了一个概念叫 substitution effect. 这其实是一个统计学概念 collinearity. 这是指一个feature 的 importance 因为出现了另一个 feature 而变低了. 在上一次打卡的时候我提出了类似的疑惑, 我们怎么保证这些feature不是因为一些奇怪的代数关系所以看起来很important的呢? 一种方法是做 PCA 分解. 主成分分解我从来都没看懂过. 大概的意思是把这些东西分解成正交的, 这样就保证了feature之间不会有关联. 

另一种方法是 mean decrease impurity 适用于决策树上. 每次决策的时候尝试去降低 impurity, 根据降低的能力来决定 feature importance. 所有 feature importance 和为 1.