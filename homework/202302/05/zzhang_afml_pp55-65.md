# AFML: 55 - 65

### Ch 4 Sample Weights

4.1

- observation不是IID的，而很多ML model会假设IID

4.2

- sample 的horizon必须得overlap，但overlap就会导致non-IID

4.4

- 计算一个值，$\mathbb{1}_{t,i}$: 如果$[t_{i,0},t_{i,1}]$ 和 $[t-1,t]$ overlap，那就置为1。
- 计算unique uniqueness of label 
    - $u_{t,i} = \mathbb{1}_{t,i}/c_t$, where $c_t=\sum_{i=1}^I \mathbb{1}_{t,i}$ 
    - average uniqueness of label i: $\bar{u}_i=(\sum_{t=1}^T u_{t,i})/(\sum_{t=1}^T\mathbb{1}_{t,i})$
    - $\bar{u}_i$ 会用到未来的信息！注意只在训练集作为label information用

4.5 Bagging classifier and uniqueness

- 不正确地假设IID，会导致oversampling
- 用Bagging Classifier 的时候设置一个max_samples，让in-bag observation 不要被sample太频繁（比它的uniqueness高很多）

4.5.1 Sequential Bootstrap

- draw 下一个observation的时候，减小那些overlap的observation被sample到的概率

