# AFML: pp 30-40

##### Information Bars

1. Tick Imbalance bars (TIB)

    - $b_t=1$ 如果上涨，$b_t=-1$ 如果下跌，保持的话就和$b_{t-1}$一样，$t$ 表示一个tick
    - $\theta_T=\sum_{t=1}^Tb_t$ 表示累计的signed ticks

    - $$T^* =\arg\min_T\{\|\theta_T\|\ge \mathbb{E}_0[T]*\|2\mathbb{P}[b_t=1]-1\|\}$$
    - 超过threshold 就构成一个bar。其中 $\mathbb{E}_0[T]$ 和 $\|2\mathbb{P}[b_t=1]-1\|$ 都是期望值，可以从之前的bars里算

2. Volume/Dollar Imbalance bars (VIB, DIB)

    - $v_t$ 表示 t 这个tick的volume或者dollar
    - $\theta_T=\sum_{t=1}^Tb_tv_t$ 注意每个tick $b_tv_t$ 有正有负
    - $v^+=\mathbb{P}[b_t=1]\mathbb{E}_0[v_t|b_t=1]$ 上涨的时候期望volume
    - $$T^* =\arg\min_T\{\|\theta_T\|\ge \mathbb{E}_0[T]*\|2v^+-\mathbb{E}_0[v_t]\|\}$$

3. Tick Run Bars (TRB)
    - 只考虑单边的accumulated signed ticks
    - $\theta_T=\max\{\sum_{t|b_t=1}^Tb_t,-\sum_{t|b_t=-1}^Tb_t\}$
4. Volume/Dollar Run Bars (VRB, TRB)
    - 只考虑单边的累计volume/dollar
    - $\theta_T=\max\{\sum_{t|b_t=1}^Tb_tv_t,-\sum_{t|b_t=-1}^Tb_tv_t\}$

##### ETF trick 处理多product

- 适合包含很多instrument的操作，比如 [future spread](https://www.cmegroup.com/education/courses/understanding-futures-spreads/futures-spread-overview.html)

- 之前的方法弊端

    - spread 交易有一个 weight-induced convergence 现象（不太懂），会mislead 模型
    - spread可以有negative值，只考虑正值的模型无法处理
    - 包里的instrument可能交易时间不align

- 解决方案：

    - 考虑 a time series that reflects the value of $1 invested in a spread
    - 表示了PnL的change，是strictly positive的（因为是一个比例，可以用(1+r).cumprod() 得到非负series）

- 一些 Notation

    - $K_t$ 表示 $1 investment value

    - $i\in[1,I]$ instrument, $t\in[1,T]$ bar，开$o_{i,t}$, 收$p_{i,t}$，汇率$\varphi_{i,t}$，volume $v_{i,t}$，carry benefit/cost $d_{i,t}$, 

    -  $w_t$ ：Allocation vector on bars $B\subseteq\{1,\cdots,T\}$ B 只包含一段时间

- $t$ 时刻的holding: $h_{i,t}=\frac{K_t}{o_{i,t+1}\varphi_{i,t}}\times\frac{w_{i,t}}{\sum_{i=1}^I |w_{i,t}|}$ if $t\in B$ else $h_{i,t-1}$ 
    - 注意点：用了$o_{i,t+1}$而不是$p_i,t$ 因为对于期货我们可能在roll time t 不知道 $p_{i,t}$（没明白）
- $t$ 时刻 market value 改变：$\delta_{i,t}=p_{i,t}-o_{i,t}$ if $(t-1)\in B$ else $\Delta p_{i,t}$
    - 这里考虑的是$B$这一段里我们考虑 profit/losses 会reinvest
- t 时刻的 \$1 investment value 就是 $K_t=K_{t-1}+\sum_{i=1}^Ih_{i,t-1}\varphi_{i,t}(\delta_{i,t}+d_{i,t})$
    - 相当于就是前一时刻的 # 乘上 price difference per #
- 其他细节：Rebalance cost, bid-ask spread 就考虑要交易的量等等
-  volume 用的是 basket 里交易最不活跃的member来代表： $v_t=\min_{i}\{\frac{v_{i,t}}{|h_{i,t-1}|}\}$ 

##### PCA Weights

- 主要idea就是通过allocation vector $w$ weighted的 $\sigma^2$ map到主成分vector上
- 尽可能给eigenvalue小的component分配更多的risk ($\sigma^2$)

##### Single Future Roll

- 主要考虑的是 future roll的时候的return有正有负，但想要non-negative  series
- 处理方法就是先算 return $r$ (rolled price change / previous raw price)，然后用 $(1+r).cumprod()$.

##### Sampling 生成新bar 

- Event-based sampling

    - 有了observation $\{y_t\}_{t=1,\cdots,T}$ 之后

    - $S_t=\max\{S_t^+,S_t^-\}$ signal >= h 的时候可以生成新的bar
        - 相当于 累计的 $\sum_{i=\tau}^t(y_i - E_{i-1}[y_t])\ge h$ 时就构造一个新的bar，注意这儿 $\tau \in[1,t]$ 即可，非从头开始
        - $S_t^+=\max\{0, S_{t-1}^+ + y_t - E_{t-1}[y_t]\}$
        - $S_t^-=\max\{0, S_{t-1}^- + y_t - E_{t-1}[y_t]\}$
        - CUSUM filter里 $E_{t-1}[y_t]=y_{t-1}$

