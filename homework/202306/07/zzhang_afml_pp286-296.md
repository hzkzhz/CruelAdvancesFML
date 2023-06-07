# AFML: pp 286 - 296

##### 19.4 Second Generation: Strategic Trade Models

- 更关注illiquidity => 关注signed volume和order flow imbalance
- 作者认为 微结构估计的 t-value 比估计本身更informative

##### 19.4.1 Kyle's Lambda

- 假设有一个资产value：$v\sim N(p_0, \Sigma_0)$
- order flow的总数为：$y = u + x$
    - noise trader 交易总数：$u\sim N(0, \sigma_u^2)$
    - informed trader 知道 v，并且demand总数为 x
    - 做市商按照 order flow imbalance来调整价格
- informed trader猜测做市商的价格设定为 $p=\lambda y +\mu$, $\lambda$ 用来衡量illiquidity的程度（越小，流动性越好）。informed trader的profit为 $\pi=(v-p)x$，在$x=\frac{v-\mu}{2\lambda}$ 处最大
- 做市商推测 informed trader的demand是：$x = \alpha + \beta v$ => $\alpha=-\frac{\mu}{2\lambda}, \beta=\frac{1}{2\lambda}$  是按照上面那个informed trader maximum profit算出来的。
- equilibrium 成立的唯一情况
    - $$\mu = p_0$$, $\alpha=p_0\sqrt{\sigma_u^2/\Sigma_0}$, $\lambda=1/2\sqrt{\Sigma_0/\sigma_u^2}$, $\beta=\sqrt{\sigma_u^2/\Sigma_0}$
    - informed trader的收益为：$E[\pi]=\frac{1}{4\lambda}(v-p_0)^2$
    - 所以收益和 （1）misprice $v-p_0$；(2) noise trader的variance，越高，informed trader的收益越高；(3) 1/$\Sigma_0$ 即证券的variance，越低，informed trader的收益越高
    - $\lambda$ 包含了price impact，可以用回归来估计 
        - $\Delta p_t = \lambda (b_tV_t) + \epsilon_t$ ， $p_t$ 是价格序列，$b_t$ 是 aggressor flag序列，$V_t$ 是volume序列

##### 19.4.2 Amihud's Lambda

- $$|\Delta \log \tilde{p}_\tau| = \lambda \sum_{t\in B_\tau} (p_tV_t) + \epsilon_\tau$$
    - 其中 $\tilde{p}_\tau$ 是close price of bar $\tau$. 
- 有很高的rank correlation to intraday estimates of effective spread.

##### 19.4.3 Hasbrouck's Lambda

- 根据的是 trade-and-quote data

- $\log \tilde{p}_{i,\tau} - \log\tilde{p}_{i,\tau-1}=\lambda_i \sum_{t\in B_{i,\tau}} (b_{i,t}\sqrt{p_{i,t}V_{i,t}}) + \epsilon_{i,\tau}$
    - $i$ 表示 security i
- 可以用$\lambda_i$ 作为估计effective cost of trading (market impact)的特征

##### 19.5 Third Generation: Sequential Trade Models

- 假设有随机的independent trader到达market
- 这个模型在做市商间比较流行，因为需要估计各个rate以及event

##### 19.5.1 Probability of Information-based Trading

- game between market makers and position takers
- 初始价格是$S_0$，有$\alpha_t$ 的概率在t时刻有新的消息，其中$\delta$ 概率是坏消息，坏消息导致价格变为$S_B$，好消息有$1-\delta$概率，好消息导致价格变为$S_G$
    - $E[S_t] = (1-\alpha_t)S_0+\alpha_t[\delta_t S_B + (1-\delta_t)S_G]$
- 按照泊松分布的概率，informed trader以rate $\mu$ 到达，uninformed trader以rate $\epsilon$ 到达。
    - 则做市商会给bid price: 
        - $E[B_t] = E[S_t]-\frac{\mu\alpha_t\delta_t}{\epsilon+\mu\alpha_t\delta_t}(E[S_t]-S_B)$
    - ask price:
        - $E[A_t]=E[S_t] + \frac{\mu a_t (1-\delta_t)}{\epsilon + \mu \alpha_t(1-\delta_t)}(S_G-E[S_t])$
- 推导：breakeven bid-ask spread:
    - $E[A_t-B_t]=\frac{\mu a_t (1-\delta_t)}{\epsilon + \mu \alpha_t(1-\delta_t)}(S_G-E[S_t])+\frac{\mu\alpha_t\delta_t}{\epsilon+\mu\alpha_t\delta_t}(E[S_t]-S_B)$
    - 如果好坏时间的概率相同，即1/2，则$E[A_t-B_t]=\frac{\alpha_t\mu}{\alpha_t\mu + 2\epsilon}(S_G-S_B)$
    -  也就是决定market maker提供双边价格的依据主要是 $PIN_t=\frac{\alpha_t\mu}{\alpha_t\mu + 2\epsilon}$
    - $\alpha_t$ 和 $\delta_t$ 都是某一个时刻估计的
- 需要估计四个变量 $\alpha,\delta,\mu,\epsilon$
-  fit 一个 mixture of three Poisson distributions，具体那个P[., .]没太看懂。
    - $$P[P^B,V^S] = (1 − 𝛼)P[V^B, 𝜀]P[V^S, 𝜀]+𝛼(𝛿*P[V^B, 𝜀]P[V^S, 𝜇 + 𝜀] + (1 − 𝛿)P[V^B, 𝜇 + 𝜀]P[V^S, 𝜀])$$

##### 19.5.2 Volume-Synronized Probability of Informed Trading

- $E[V^B - V^S]=\alpha\mu[1-2\delta]$
- 对足够大的$\mu$ 有 $E[V^B-V^S]\approx \alpha\mu$
- 可以有一个对PIN的高频估计 => 跟volume clock相关. $\frac{1}{n}\sum_{\tau=1}^n|V_\tau^B-V_{\tau}^S|\approx \alpha\mu$
- $\frac{1}{n}\sum_{\tau=1}^n(V_\tau^B+V_\tau^S)=V=\alpha\mu+2\epsilon$ 
- $VPIN_\tau =\frac{\sum_{\tau=1}^n|V_\tau^S - V_\tau^S|}{nV}$
- VPIN 不是很好的volatility predictor，但还是有点预测能力的。

##### 19.6 Additional features From Microstructural Datasets

- 还有一些alternative特征，需要运用ML

##### 19.6.1 Distribution of Order Sizes

- 人trader通常会用round trade sizes，比如5、10、20、25的倍数
- 记录round-sized trades的normal frequency，然后监视deviation
- round trade sizes比平常比例大 => trend；小 => 价格通常很快会调转，因为算法交易通常不会hold long-term views

##### 19.6.2 Cancellation Rates, Limit Orders, Market Orders

- quote取消的比例很高 => 流动性比较低，参与者并没有激进地希望自己的quote被fill
- 四种掠夺性的算法：
    - Quote stuffers: 发布奇奇怪怪的单子，扰乱其他算法，唯一目的是减慢竞争算法的速度
    - Quote danglers：迫使被squeeze的trader来追逐一个不符合他利益的价格
    - Liquidity squeezer：另一个大投资者被迫平仓时，同一个方向交易，消耗流动性
    - Pack hunters：形成一个群体，以最大限度地提高触发级联效应的机会
- 可以通过quote 取消的比例和order类型来逆向选择做市商

##### 19.6.3 Time-Weighted Average Price Execution Algorithms

- 识别针对特定TWAP（时间加权均价）的算法的存在
- 相当于识别是否有trader在拆大单交易
- 可以按照：x：second, y: hour of the day, z: aggregate volume。如果每个小时都有pattern：每分钟的前几秒有比较大的volume => 可以去front-run别的大单交易者

##### 19.6.4 Options Markets

- 研究stock和option的微观结构信息研究两个市场中的分歧

- 分歧倾向于以有利于股票报价的方式解决，这意味着期权报价不包含具有重要经济意义的信息。期权交易包含股票价格中未包含的信息。
- 有比较贵的call的股票会比有比较贵的put的股票每周表现好50bp。<= 在期权流动性高，股票流动性低时预测能力更好些
- 期货的价格只体现未来价值的期望/mean，但是期权价格可以得到一个distribution。可以通过期权交易数据得到的put-call implied stock price, greek letters等等用ML算法得到

##### 19.6.5 Serial Correlation of Signed Order Flow

- order sign自相关很多天 => 羊群效应 或者 拆单
    - 几个小时内的orde sign 子相关基本就是由拆单导致的
- 可以用signed volume 序列相关性得到strength of such persistency，它也会影响order flow imbalance

##### 19.7 What is microstructural information?

- 预测做市商是否能盈利的模型的cross-entropy越高，做市商越可能做 uninformed forecast，也就是面临informed trader的概率更高
- 所以如果作为做市商需要估计自己被informed trader逆向选择的概率，合理确定bid-ask spread 
