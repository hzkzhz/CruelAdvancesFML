# AFML: pp 99-100

- 建议训练随机森林的时候，用PCA of the features，能够加速训练且减少overfitting

##### 6.5 Boosting

- 开始sample有相同的sample weight，训练一个estimator，如果它的acc超过threshold就保留这个estimator，然后给分错的observations更多的weight，再sample，fit一个新的estimator，不断的重复直到有N个estimator。最后ensemble的时候把几个estimator的输出weighted average一下，weight和每个estimator的accuracy成正比。

##### 6.6 Bagging vs. Boosting in Finance

- Boosting既能降低variance又降低bias；但是有更大可能overfit
- Bagging更好地解决overfit，Boosting更好地解决overfit。一般Overfit更难解决。
- Financial applications中更多用Bagging.
