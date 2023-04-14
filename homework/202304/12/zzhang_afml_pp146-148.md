# AFML:pp 146-148

##### 10.6 Dynamic Bet Sizes and Limit Prices

- 介绍了如何调整bet size当市场价格$p_t$ 和预测价格$f_i$ 变动的时候。

- 设 $q_t$ 是当前的仓位，$Q$ 是最大的仓位大小，$\hat{q}_{i,t}$ 是和预测值$f_i$ 相关的目标仓位大小，则

    - $\hat{q}_{i,t}=\text{Int}[\ m[w, f_i-p_t]*Q\ ]$
    - 其中$m[w,x]$ 是bet size，在 (-1,1) 之间 $m[w,x]=\frac{x}{\sqrt{w+x^2}}$
    - $x=f_i-p_t$ 表示当前市场价格和预测值的divergence。
    - $w$ 是一个调整sigmoid function的参数
    - Int[.] 取整数值
    - 当 $p_t\to f_i$，则我们的bet size $\hat{p}_{i,t}\to 0$ 来realize the gain

- 给定$(x,m^*)$其中$x=f_i-p_t$ 以及 $m^*=m[w,x]$，则可以通过这两个值得到$w$:

    - $w=x^2(\frac{1}{(m^*)^2}-1)$

-  对于order size $\hat{q}_{i,t}-q_t$ 有一个breakeven **limit price** $\bar{p}$: 

    $$\bar{p}=\frac{1}{|\hat{q}_{i,t}-q_t|}\sum_{j=|q_t+\text{sgn}[\hat{q}_{i,t}-q_t]|}^{|\hat{q}_{i,t}|}L[f_i,w,\frac{j}{Q}]$$

    - 其中$L[.]$ 是通过 $w$ 和 $f_i-p_t$得到的$p_t$
    -  $L[f_i,w,\frac{j}{Q}]=f_i-m\sqrt{\frac{w}{1-m^2}}$ 

- 除了用sigmoid function $m[w,x]=\frac{x}{\sqrt{w+x^2}}$ 我们还可以用 power function
    - $\tilde{m}[w,x]=\text{sgn}[x]*|x|^w$, $w\ge0,x\in[-1,1]$

###### Snippet 10.4 作用

- 计算仓位大小和limit price:
    - 第一步，calibrate sigmoid function $x=10$和$m^*=0.95$得到$w$值
    - 第二步，对于$Q=100,f_i=115,p_t=100$ 计算目标仓位$\hat{q}_{i,t}$.
    - 第三步，通过$\hat{q}_{i,t}-q_t = 97$ 来计算limit price 为 $p_t<112.365<f_i$ 

