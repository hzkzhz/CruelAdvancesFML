# AFML: pp 229 - 230

##### 16.4.2 Quasi-Diagonalization

- 重构covariance matrix的rows 和 columns，使得最大的值在对角线上
-  inverse-variance allocation is optimal for a diagonal covariance matrix 

##### 16.4.3 Recursive Bisection

- 不停地分items

- 开始每个unit都是 1，有一个list L 然后按照二分法划分
- $L_i$ 被划分成 $L_i^{(1)}$ 和 $L_i^{(2)}$，则有 它 $L_i^{(j)}$ 的variance 定义为 $\tilde{V}_i^{(j)}=\tilde{w}_i^{(j)}V_i^{(j)}\tilde{w}_i^{(j)}$，其中 $V_i^{(j)}$ 是 $L_i^{(j)}$ 组成部分们的covariance，$\tilde{w}_i^{(j)}=diag[V_i^{(j)}]^{-1}\frac{1}{tr[diag[V_i^{(j)}]^-1]}$ 。然后计算 $\alpha = 1 - \frac{\tilde{V}_i^{(1)}}{\tilde{V}_i^{(1)}+\tilde{V}_i^{(2)}}$。则 每一个 $L_i^{(1)}$ 里的item，weight都乘 $\alpha$，$L_i^{(2)}$ 里的都乘$(1-\alpha_i)$。



