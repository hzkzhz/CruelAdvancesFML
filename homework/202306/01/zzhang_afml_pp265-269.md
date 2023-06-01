# AFML: pp 265 - 269

##### 18.4 Lempel-Ziv(LZ) Estimators

- LZ algorithm 可以把message 分解成 non-redundant substrings
- 用 LZ 分解后的substring个数 / message总长度 来表示compression rate
- Kontoyiannis 1998 另一种match：
    - $L_i^n= 1+\max \{l | x_i^{i + l} = x_j^{j + l} \text{for some} i - n \le j \le i - 1, l\in[0,n]\}$
    - 计算相同序列的长度，可以有overlap，n可以是常数也可以等于 i 
    - 用$\text{avg}\frac{L_i^n}{\log_2n}=\frac{1}{H}$ 来估计 entropy H。high entropy 有更短的non-redundant substring
- Sliding-window LZ estimator: $\hat{H}_{n,k}=[\frac{1}{k}\sum_{i=1}^k\frac{L_i^n}{\log_2n}]^{-1}$

- increasing window LZ estimator $\hat{H}_{n}=[\frac{1}{n}\sum_{i=2}^n\frac{L_i^i}{\log_2n}]^{-1}$

- 以上要求process：stationary, ergodicity, takes finitely many values, satisfy Doeblin condition
- 修改后的：
    - $\tilde{H}_{n,k}=\frac{1}{k}\sum_{i=1}^k\frac{\log_2n}{L_i^n}$
    - $\tilde{H}_{n}=\frac{1}{n}\sum_{i=2}^n\frac{\log_2n}{L_i^i}$
    - 选择 合适的 n s.t. $N\approx n + (\log_2 n)^2$
- $\hat{H}[X]\to$ Shannon's entropy as $n\to \infty$
- 如果 message太短了可以重复几次，可能可以倒转string

