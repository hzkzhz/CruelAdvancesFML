# AFML: pp 69-70

#### 4.6 return attribution

- 之前考虑的是怎么sample数据，让它近似IID，这里是给sample一些weight （importance）
- 给 return绝对值大的sample更大的weight
- $\tilde{w}_i=|\sum_{t=t_{i,0}}^{t_{i,1}}\frac{r_{t-1,t}}{c_t}|$ 也就是这一个event（持续时间为$[t_{i,0},t_{i,1}]$）的基于return和uniqueness的weight
    - 还是需要normalize一下，让平均的weight是1. 
    - $w_i=\frac{\tilde{w}_i}{\sum_{i=1}^I\tilde{w}_j}*I$

**Determination of sample weight by absolute return attribution (Snippet 4.10)**

- return 用的是 log return
- 返回的是weight的absolute value

#### 4.7 Time decay

- 越老的数据越不重要 需要一个 time decay factor $d[x] > 0, \forall x\in[0,\sum_{i=1}^I \bar{u}_i]$

- 按照cumulative uniqueness 来decay，而不是按时序decay，不然decay太快了
- 最新的数据，decay factor 是 1 （没有decay） ：$d[\sum_{i=1}^I \bar{u}_i]=1$
    - 用户给定数值 $c\in(-1,1]$
        - 如果 $c\in[0,1]$: $d[0]=c$  （书上写的和后面的演算有点矛盾，这里从书上的$d[1]=c$改成了$d[0]=c$）, 更大的就是 linear decay
        - 如果 $c\in(-1,0)$: 分段decay： $d[x]=0,\forall x\le -c\sum_{i=1}^I\bar{u}_i$. 比 $-c\sum_{i=1}^I\bar{u}_i$ 大的就linear decay。 
        - 综合来说，都是分段的linear decay，所以 $d$ 可以表示成 $d=a+bx$ 来表示
            - 由条件：$d[\sum_{i=1}^I \bar{u}_i]=1$ 条件得 $a = 1 - b\sum_{i=1}^I \bar{u}_i$
            - 如果 $c\in[0,1]$ 有 $d=a+b0=c$ 得 $1-b\sum_{i=1}^I \bar{u}_i=c$ 得到 $b=\frac{1-c}{\sum_{i=1}^I \bar{u}_i}$ 
            - 如果 $c\in(-1,0)$ 有 $d=a-bc\sum_{i=1}^I \bar{u}_i=0$ 得到 $b=[(c+1)\sum_{i=1}^I \bar{u}_i]^{-1}$

**Implementation of time-decay factors (snippet 4.11)**

- `clfW` 就是updates的前缀和，所以`clfW.iloc[-1]` 就是 $\sum_{i=1}^I \bar{u}_i$

- `slop` 就是上面式子里的 b，`const` 是式子里的 a

    
