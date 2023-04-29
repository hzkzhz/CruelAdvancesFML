# AFML: pp 173-175

##### 13.5 Numerical Determination of Optimal Trading Rules

- OTR:  optimal trading rule 

##### 13.5.1 The Algorithm

第一步：通过 $P_{i,t}=(1-\varphi)E_0[P_{i,T_i}]+\varphi P_{i,t-1}+\sigma\epsilon_{i,t}$ 来估计 $\{\sigma, \varphi\}$:

- $P_{i,t} = E_0[P_{i,T_i}] + \varphi(P_{i,t-1}-E_0[P_{i,T_i}])+\xi_t$
- 使$X = [P_{0,0}-E_0[P_0,T_0],\cdots, P_{I,T-1}-E_0[P_{I,T_I}]]^T$, 
- $Y=[P_{0,1},\cdots,P_{I,T}]^T$, $Z=[E_0[P_{0,T_0}],\cdots,E_0[P_{I,T_I}]]^T$
- 用OLS可以得到 $\hat{\varphi}=\frac{cov[Y,X]}{cov[X,X]}$, $\hat{\xi}_t = Y-Z-\hat{\varphi}X$, $\hat{\sigma}=\sqrt{cov[\hat{\xi}_t,\hat{\xi}_t]}$

第二步：构造一个mesh of $(\underline{\pi},\bar{\pi})$ 表示20x20的选择

第三步：根据$\{\hat{\sigma},\hat{\varphi}\}$生成100,000条 $\pi_{i,t}$ 的path，限制holding period（比如100个observation）

第四步：把这100,000条path用20x20不同的 $(\underline{\pi},\bar{\pi})$ 跑一遍，计算sharpe ratio

第五步：

- 5a：选择最optimal的$(\underline{\pi},\bar{\pi})$ 
- 5b：如果已经决定了profit target $\bar{\pi}_i$，用这个信息和第四步的结果决定$\underline{\pi_i}$
- 5c：如果已经决定了 stop-loss $\underline{\pi_i}$，用这个信息和第四步的结果决定 $\bar{\pi}_i$

Half-life of the process?

- $\tau=-\frac{\log2}{\log\varphi}, \varphi\in(0,1)$

##### 13.5.2 Implementation

- 略
