# AFML: pp 113 - 126

### Ch 8: Feature Importance

##### 8.1 Motivation

- 简单来说就是如果试了很多次（>20次），找到一个significance > 5%的，其实并不能用。如果尝试的次数多，significance这个threashold应该提更高，比如1%等

##### 8.2 The importance of feature importance

找feature的时候值得问的问题：

- Are these features important all the time, or only in some specific environments?
- What triggers a change in importance over time?
- Can those regime switches be predicted?
- Are those important features also relevant to other related financial instruments?
- Are they relevant to other asset classes?
- What are the most relevant features across all financial instruments?
- What is the subset of features with the highest rank correlation across the entire investment universe?

思考这些问题比foolish backtest cycle好多了。

##### 8.3 Feature Importance with Substitution Effects

Substitution effects: 相当于 multi-collinearity

- 解决方案：PCA

##### 8.3.1 Mean Decrease Impurity (MDI)

- Explanatory-importance (in-sample, IS) metod => tree-based classifiers
- 如果有很多棵树，可以把各个树里面feature的overall impurity decrease取个平均值然后rank 一下feature的importance

用MDI时候需要注意的点：

1. 如果一些feature没有被tree选中，会有Masking effects，即它的impurity decrease是0
    - 用sklearn的RF是设置`max_features=int(1)` ，每个level只有一个random feature被选中
    - 每个feature都有机会被选中去split node
    - 如果某一棵树里feature importance是0，拿去计算average impurity decrease的时候忽略这个0
2. procedure是in-sample的，每个feature即使没有predictive power也有一些importance
3. MDI没法用在其他non-tree based classifier上
4. MDI有个好处是每个feature的importance在0-1，且加起来是1
5. MDI没有考虑substitution effects，而且会削减共线性的feature的importance
6. 可能会biased to有很多category的feature

- Sklearn的RandomForest默认的feature importance metric就是MDI

##### 8.3.2 Mean Decrease Accuracy (MDA)

- slow, predictive-importance (out-of-sample, OOS) method
- 第一步，训练一个分类器； 第二步，根据一些metrics（Acc、negative log=loss）derive出它的out-of-sample performance； 第三步，对feature矩阵 (X) 的每一列进行置换，一次一列，在每一列置换后得出out-of-sample performance。 feature的重要性是 function of 其column's permutation 引起的performance loss。

注意点：

1. 适合任何classifier，不一定是tree-based classifier
2. 不止适合Acc，还适合其他metrics，比如F1
3. 还是容易受subsitution effect影响。给两个一样的feature，它会认为其中一个是完全可以被另一个替代的（确实），但也同样会认为这两个feature都没用，即使他们实际上是有用的
4. MDA可能会认为所有feature都是unimportant的
5. Cross validation需要purge and embargo

##### 8.4 Feature Importance without Substitution Effects

##### 8.4.1 Single Feature Importance (SFI)

- Cross-section predictive importance (OOS)

注意点：

1. 不局限于tree
2. 不只是accuracy
3. 不受substitution effects影响
4. 可能认为所有feature都是unimportant的

缺陷：

1. 没法说明joint importance，比如feature B只有在feature A也存在的时候importance，用SFI就发现不了了
    - 一个解决方案是计算subset of features的OOS performance score

##### 8.4.2 Orthogonal Features

- 缓解substitution effects => orthogonalize the features (比如PCA)

步骤：

1. 特征矩阵$\{X_{t,n}\}$ standardize => Z
2. 计算Z的特征值和特征向量 $Z'ZW=W\Lambda$
3. 生成正交的特征：$P=ZW$
    - $P'P=W'Z'ZW=W'W\Lambda W'W=\Lambda$

先standardization的意义：

- centering the data: 使得first principal component oriented in the main direction of the observation
- rescaling: 使得PCA关注于correlation，如果不这样的话，first principal components 被variance最大的feature dominate

用orthogonal的一大好处是

- 你可以去验证你用比如SFI、MDA找的feature真的是important的（它们一起组成了PCA找到的important的feature的很大一部分）🌟

计算correlation between PCA rank的feature和MDI等其他方法找到的feature：

- 用weighted Kendall's tau更好

##### 8.5 Parallelized vs. Stacked Feature Importance

方法1: 计算每个security $(X_i,y_i)$对应的feature的importance，然后average across different securities得到这个feature的importance

- parallelize 算起来比较快
- 会受substitution effect的影响，feature rank会有一些变动，增加了variance，不过average之后可以忽略

方法2: 把securities组成一个大的matrix $(X,y)$，其中$\tilde{X}_i$ 是transformed instance of $X_i$ (比如standardized on a rollling trailing window => ensure some distributional homogeneity $\tilde{X}_i\sim X$)，然后直接计算importance

- 不需要weighting scheme
- 更general，less biased by 异常值和overfitting
- 因为没有把importance score average，所以substitution effect不会让这些score降很多
- stacking更好一点，因为减少了overfitting 某一个security的可能，缺点就是需要更多的memory

##### 8.6 Experiments with Synthetic Data

一些代码，先略。
