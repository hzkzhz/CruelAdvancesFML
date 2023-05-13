# AFML: pp 223 - 228

##### 16.4 From Geometric to Hierchical Relationships

- quadratic optimizers不稳定的一个原因：vector space被建模为一个完整的（完全连接的）图，其中每个节点都是替代另一个节点的alternative
    - => 需要 drop unnecessary edges
- 用correlation去做分散投资缺少了group的考虑 => 需要hierarchy
    - 用树模型 => 从上到下分配weights
- 要介绍 Hierarchical Risk Parity methdo (HRP)
    - 三部分：tree clustering, quasi-diagonalization, recursive bisection

##### 16.4.1 Tree Clustering

- T x N matrix of observations

- 1. N x N correlation $\rho_{ij}=\rho[X_i,X_j]$

    - distance: $d_{ij}=\sqrt{1/2(1-\rho_{ij})}$

- 2. Eucliean distance btween two column-vectors $\tilde{d}_{ij}=\sqrt{\sum_{n=1}^N (d_{ni}-d_{nj})^2}$

- 3. Cluster pair of columns $(i,j)$ 拥有最小的 $\tilde{d}_{ij}$ => 标记为 cluster $u[1]=(i,j)$

- 4. 计算和cluster的距离：$\dot{d}_{i,u[1]}=\min[\{\tilde{d}_{ij}\}_{j\in u[1]}]$ 

- 5. 给矩阵 $\{\tilde{d}_{ij}\}$ append $\dot{d}_{i,u[1]}$ 作为新的行和列，然后把cluster $u[1]$的行和列删去

- 6. 重复3，4，5，一直append N-1这样的clusters，直到变成2x2矩阵（包含所有的original item）

可以使用

```python
import scipy.cluster.hierarchy as sch
dist = ...
link = sch.linkage(dist, 'single') # linkage matrix
```

生成了一个 $(N-1)\times 4$ 的矩阵 $Y=\{(y_{m1},y_{m2},y_{m3},y_{m4}\}_{m=1,\cdots,N-1}$，其中

- $y_{m1},y_{m2}$ 是cluster，$y_{m3}=\tilde{d}_{y_{m1},y_{m2}}$
- $y_{m4}\le N$ 表示cluster m里含有的original item
