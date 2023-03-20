# AFML: p 98

##### 6.4 Random Forest (RF)

- 比bagging多加了一层randomness：
    - 优化每个节点拆分时，只会评估random subsample of attributes（无替换）
- 好处：
    1. 减少overfitting
    2. evalutes feature importance
    3. provides out-of-bag acc estimate
- 缺陷：
    - 与 bagging 一样，RF 不一定会表现出比单个决策树更低的bias。
    - 如果samples很多redundant，还是会有overfitting
- 建议：
    - 每棵树的feature少一点
    - regularization的参数大一点
    - `max_ samples` is set to the average uniqueness (`avgU`) between samples.
    - 修改RF，把默认的标准bootstrap换成sequential bootstrap
