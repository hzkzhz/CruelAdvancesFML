# AFML: pp 103 - 110

### Ch 7: Cross-Validation (CV) in Finance

##### 7.1 Motivation

- CV => 防止overfitting
- 但是Finance里，standard CV甚至会通过超参数调整导致overfitting

##### 7.2 The goal of cross-validation

- Learn the general structure of the data
- K-fold CV: 把dataset分成K份，K个iteration，每个iteration i，其中第i份data作为test data，另外(K-1)份为training data

##### 7.3 Why K-fold CV fails in finance (leakage)

原因1: observations不是从IID process里draw的

原因2: testing set在开发模型的过程中被多次使用，导致multiple testing and selection bias

这一节先关注原因1 => leakage

- serial correlation => $X_t\approx X_{t+1}$
- labels are derived from **overlapping datapoints** => $Y_t\approx Y_{t+1}$

两个解决方案 reduce the likelihood of leakage:

1. 去掉训练集中的observation $i$ 如果用来预测$Y_i$的信息有一部分用来预测测试集中的$Y_j$，比如$Y_i$和$Y_j$ 不应该有overlapping period
2. 避免过拟合classifier: a) early stop the base estimator; b) bagging并且控制oversampling on redundant examples: b.1)设置`max_samples == average uniqueness` b.2) sequential bootstrap

小更正：

- 只有当$(X_i,Y_j)\approx (X_j,Y_j)$的时候才有leakage发生，如果只有$X_i\approx X_j$ 或者 $Y_j\approx Y_j$ 不能说有leakage （i 在training set里，j在test set里）

##### 7.4 A solution: Purged K-fold CV

- purging: 从训练集中清除所有标签在时间上与测试集中包含的标签重叠的observation。
- embargo: 从训练集中消除紧跟在测试集中的observation之后的observation （因为serial correlation问题）

##### 7.4.1 Purging the Training Set

- 简单来说就是去掉和测试集用到的时间overlap的训练集数据
- 如果有leakage，那k-fold CV，k越大“实验结果”越好，因为测试集里的数据和训练集里的overlap越多
- 处理好了leakage的话（用purging），k越大，结果还是会越好，因为recalibrate了更多次，但是到一定k*之后，效果不会再增加了

##### 7.4.2 Embargo

- 去掉test set之后的observation
- 生成test data的时候用range $[t_{j,0},t_{j,1}+h]$，多取 $h$，让之后的training set被purge掉。$h\approx 0.01T$ 即可。

##### 7.4.3 The purged K-fold class

- 不止建立模型的时候要用purge和embargo，在hyper-parameter fitting, backtesting, or performance evaluation都需要这样做。

##### 7.5 Bugs in sklearn's CV

- Scoring functions do not know `classes_`
- `cross_val_score` will give different results because it passes weights to the fit method
    - 用自己写的`cvScore` 而不是`cross_val_score`

