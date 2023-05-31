# AFML: pp 263 - 265

##### 18.1 Motivation

- 预测price series里面包含的信息多少
    - 如果信息少，用momentum bets更优
    - 如果信息多，用mean-reversion bets更优

##### 18.2 Shannon's entropy

- entropy：一个stationary source of data 中包含的平均信息量
- 离散随机变量X 可以取数值 $x\in A$，则它的entropy为：
    - $$H[X]=-\sum_{x\in A} p(x)\log_2 p(x)$$
    - $0\le H[X]\le \log_2|A|$ 
    - H[x] = 0 如果 p(x) = 1/|A|
    - 低概率的outcome蕴含更多的信息
- Redundancy: $$R[X]=1-\frac{H[X]}{\log_2|A|}$$, $0\le R[X]\le 1$
- Mutual information 
    - $$MI[X, Y] = E_{f(x,y)}\log\frac{f(x,y)}{f(x)f(y)}=H[X]+H[Y] - H[X,Y]$$
    - = 0 如果两个变量independent
    - 如果两个变量都normally distributed，则类似 Pearson correlation, $\rho$. 
        - $$MI[X,Y]=-1/2\log (1-\rho^2)$$

##### 18.3 The plug-in (or maximum likelihood) estimator

- 有sequence $x_1^n$：表示从1-n的string；$y_1^w\in A^w$ 表示长度为 w 的word。$\hat{p}_w[y_1^w]$ 表示 $y_1^w$ 在 $x_1^n$ 里面出现的频率。
- entropy value: $\hat{H}_{n,w}=-\frac{1}{w}\sum_{y_1^w\in A^w} \hat{p}_w[y_1^w]\ \log_2 \hat{p}_w [y_1^w]$
    - 它也被叫做 maximum likelihood entropy estimator
    - w应该large enough，n需要足够大compared to w
