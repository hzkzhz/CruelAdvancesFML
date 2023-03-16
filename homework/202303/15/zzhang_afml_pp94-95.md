# AFML: pp 94-95

### 6.3 Bootstrap aggregation 

Bagging算法流程

1. 采样 N份训练集
2. 在每个训练集上训练一个estimator（共N个）
3. 把N个estimator的预测结果的平均值作为最终预测值

#### 6.3.1 Variance Reduction

Bagging可以降低预测的variance

- Notation：预测的variance: $\varphi$ 由N个estimator的variance决定，每个estimator的平均预测variance是$\bar{\sigma}$，预测器间的平均correlation是$\bar{\rho}$
    - $$\varphi=\frac{1}{N^2}\sum_{i,j}\sigma_{ij}=\frac{1}{N}(\bar{\sigma}^2+(N-1)\bar{\sigma}^2\bar{\rho})]$$

-  如果 $\bar{\rho} < 1$ 则 ensemble后的variance 小于$\bar{\sigma}^2$.
- 因此可以按照之前第四章介绍的方法经可能让sample之间的相关性更小

