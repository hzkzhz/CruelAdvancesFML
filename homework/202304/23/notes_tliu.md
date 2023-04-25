# notes

作者介绍了一种 SFI 方法，single feature importance 方法，但是网上并不是很能搜到相关的资料。

它可以用在各种分类器上，并不局限于树型的。同时它的评价指标不仅仅是 accuracy，也就是它并不是完全以提升 accuracy 为目标进行划分。没有 substitution effect。可能会把所有的feature都认为是不重要的。

orthogonal features 也可以用来解决 substitution effect，它适合于在用 MDI MDA 之前就进行这样一个操作。比较常见的算法有 PCA。虽然PCA不能完全消除 substitution effect，但是可以消除线性组合的可能。