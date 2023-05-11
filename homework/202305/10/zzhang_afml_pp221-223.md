# AFML: pp 221 - 223

#### Ch 16: Machine Learning Asset Allocation

##### 16.1 Motivation

- Hierarchical Risk Parity (HRP) 算法 能够在covariance matrix不可逆的情况下算variance小的组合
- 一个实际应用是确定跨多个机器学习 (ML) 策略的分配。

##### 16.2 The problem with convex portfolio optimization

- CLA：绕开了KKT条件，能够在有限时间找到solution。但现在很多人还是只用quadratic programming methods
- 缺陷是 预测return的小偏移就会让CLA生成很不同的portfolio，由于return很难预测准，一般会关注covariance矩阵 => 但quadratic programming会用到covariance矩阵的逆，担当covariance矩阵的condition number很大的时候容易误差很大
    - condition number：absolute value of the ratio between its maximal and minimal (by moduli) eigenvalues
    - A condition number for a matrix measures how sensitive the answer is to perturbations in the input data and to roundoff errors made during the solution process.

##### 16.3 Markowitz's curse

- 如果matrix的conditio number太高了，numerical error会让逆非常不稳定
- Markowitz's curse：投资越相关，多元化的需求就越大，但我们就越有可能得到不稳定的解决方案。 多元化的好处往往被估计误差所抵消。

- 例如，估计大小为 50 的 covaraince 矩阵至少需要 5 年的每日 IID 数据。 正如大多数投资者所知，相关结构在如此长的时期内不会以任何合理的置信水平保持不变。 
- => 即使平均weighted的portfolio都比 mean-variance或者risk-based optimization更好。

