# AFML: pp 129 - 130

### Ch 9 Hyper-Parameter Tuning with Cross-Validation

9.1

- 本章主要介绍如何用purged k-fold CV（就是把overlap都去掉之后）调超参

9.2

- 用sklearn的`GridSearchCV`的时候传入CV generator记得传`PurgedKFold`，不要用默认的，以免leak information
- 在做meta-labeling application的时候用metric `scoring='f1'`
    - 因为unbalance label: 0 class
    - 其他的可以用`accuracy`或者`neg_log_loss`
- 需要重写sklearn的Pipeline，因为之前的实现不支持sample_weight
