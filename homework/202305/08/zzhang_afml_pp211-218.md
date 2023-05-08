# AFML: pp 211 - 218

### Ch 15: Understanding Strategy Risk

##### 15.1 Motivation

- 两个leave condition：一个是profit-taking另一个是 stop-loss
- 可以把distribution of outcomes模拟成binomial process
- 本章：评估策略何时容易受到betting frequency, odds, and payouts 这些变量中任何一个的微小变化的影响。

##### 15.2 Symmetric payouts

- 假设一个strategy有 n 个IID的outcome $X_i,i\in[1,n]$ 有 profit $\pi$ with $P[X_i=\pi]=p,P[X_i=-\pi]=1-p$ 
    - 则 $E[X_i]=\pi(2p-1)$, $Var[X_i]=4\pi^2p(1-p)$, 
    - Sharpe 是 $\theta[p,n]=\frac{2p-1}{2\sqrt{p(1-p)}}\sqrt{n}$
- $\theta[p,n]$ 可以被认为是 re-scaled t-value => 只要 p 比1/2大一点，只要 n 足够大，Sharpe也会很高=>HFT的economic basis
- $p=\frac{1}{2}(1+\sqrt{1-\frac{n}{\theta^2+n}})$: 策略找到的交易机会少，就需要更高的precision (p) 才能到达相同的Sharpe

##### 15.3 Asyymetric payouts

- 其他一样，但是outcome不是对称的，而是 $\pi_+$ 和 $\pi_i$ 
    - 则 $E[X_i]=(\pi_+ - \pi_-)p+\pi_-$，$Var[X_i]=(\pi_+ - \pi_-)^2p(1-p)$ ，
    - Sharpe 是 $\theta[p,n,\pi_-,\pi_+]=\frac{(\pi_+-\pi_-)p+\pi_-}{(\pi_+-\pi_-)\sqrt{p(1-p)}}\sqrt{n}$
- 可以得到 $p=\frac{-b+\sqrt{b^2-4ac}}{2a}$
    - $a =(n+\theta^2)(\pi_+-\pi_-)^2$
    - $b=[2n\pi_- - \theta^2(\pi_+-\pi_-)](\pi_+-\pi_-)$
    - $c=n\pi_-^2$
- the strategy is vulnerable to small changes in p，所以$\pi_-$小了或者 n 小了，都需要更高的 p

##### 15.4 The probability of strategy failure

- $\pi_-$ 和 $\pi_+$ 以及 $n$ 可以被PM设定，但是 $p$ 和 $\theta^*$ 没有办法
-  $p$ 可以被model成一个RV，$p_{\theta^*}$ 是一个threshold，比它小就会underperform benchmark
- 可以计算得到，如果 $\pi_-=-0.1,\pi_+=0.05,n=260$，那么  $p_{\theta^*=0}=2/3$ 也就是说如果 p 掉一点，就等于没有profit => strategy 内在的非常risky
- Strategy risk 和 内在的 underlying portfolio risk不同

##### 15.4.1 如何计算 strategy fail的概率也就是 $P[p<p_{\theta^*}]$

- 第一步，估计$\pi_-=E[\{\pi_t|\pi_t\le0\}_{t=1,\cdots, T}]$, $\pi_+=E[\{\pi_t|\pi_t> 0\}_{t=1,\cdots,T}]$，或者用两个Gaussian 的mixture去估计
- 第二步：算 n，也就是annual frequency，用平均数估计
- 第三步：bootstrap the distribution of p，每次sample $\lfloor nk\rfloor$ 个sample（k是评估strategy的年份，比如2年），计算p，然后多这样sample几次，用Kernel density estimator来fit一个p的PDF。对于足够大的 k，我们可以用 $f[p]\sim N[\bar{p}, \bar{p}(1-\bar{p})]$ 来近似。$\bar{p}$ 就是总体的outcome >0的概率。
- 第四步：给定 $\theta^*$ 计算 $p_{\theta^*}$
- 第五步：计算$P[p<p_{\theta^*}]=\int_{-\infty}^{p_{\theta^*}}f[p]dp$

一般$P[p<p_{\theta^*}]>0.05$  就可以认为这太risky了，即使invest的instrument非常low volatility

