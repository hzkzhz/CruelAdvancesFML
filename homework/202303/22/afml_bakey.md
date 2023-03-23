# Financial Machine Learning as a Distinct Subject
## THE MAIN REASON FINANCIAL MACHINE LEARNING  PROJECTS USUALLY FAIL
* The rate of failure in quantitative finance is high, particularly so in financial ML.
### The Sisyphus Paradigm
* Discretionary portfolio managers(独立的资产管理者, 或者理解为firm里面的一个独立投资经理) make investment decisions that do not follow a particular theory or rationale.主要根据自身的判断和直接来bet
* 这里讨论的情况是：一般的投资公司会招聘50个独立的投资经理，单独进行决策，每个人根据自己的判断，常识和直觉来作出投资判断。但是50个人并不能形成一个团队，这种情况公司付给团队的成本，很有可能大于这个团队能取得的收益。
### The Meta-Strategy Paradigm
- 首先说明了要完成一个ML驱动的投资决策体系是很复杂的。因为ML是由很复杂的piplines组成，如果没有一个全局观(global view)，那么很有可能会失败。
- 所以很多成功的投资公司就会采用Meta-Strategy Paradigm。本书会教你如何搭建出来一个ML factory，通过factory来完成ML的全pipeline
## BOOK STRUCTURE
* Part 1: help you structure your financial data in a way that is amenable to ML algorithms.
* Part 2: discusses how to do research with ML algorithms on that data.
* Part 3: explains how to backtest your discovery and evaluate the probability that it is false
* Part 4:  goes back to the data and explains innovative ways to extract informative features.
### Structure by Production Chain
### Data Curators
* 负责数据的collecting，cleaning，indexing，storing，adjusting and delivering all data to the production chain.这个Team的成员由市场的微观结构(microstruct)和数据协议(data protocol，例如FIX,Financial Information eXchange)专家组成。
### Feature Analysis
* 这个阶段是把raw data转成有意义的signal。这些signal对于金融市场的变量来说，有一定的预测能力。Team member应该是infromation theory专家。
* feature analysts may discover that the probability of a sell-off particularly high when:
**  quoted offers are cancelled-replaced with market sell orders
** quoted buy orders are cancelled-replaced with limit buy orders deeper in the book
### Strategists
### Backtesters
### Deployment Team
### Portfolio Oversight
## Data Analysis
### MOTIVATION
* 主要讲如何处理unstructured financial data,产出structured data提供给ML algorithms
### ESSENTIAL TYPES OF FINANCIAL DATA
#### Fundamental Data
* 基础数据的来源有：监管文件（regulatory filings），商业分析（business analytics）。大部分为财务数据，季报。有观点认为这部分数据有一定的时效性，所以一定要及时分析。有一个初学者的认知误区是这些数据一定是在报告期末才会发布，实际上并不是。
* 个人观点：目前这些数据的收集应该都是全自动化流程处理，属于Infra的范围。

| Fundamental Data | Market Data | Analytics | Alternative Data|
| ------ | ------ | ------ | ------ |
| Assets | Price/yield/implied volatility | Analyst recommendations | Satellite/CCTV images |
| Liabilities | Volume | Credit ratings | Google searches |
| Sales | Dividend/coupons | Earnings expectations | Google searches |
| Costs/earnings | Open interest | News sentiment | Twitter/chats |
| Macro variables | Quotes/cancellations | ...| Metadata |
#### Market Data
* 市场数据包括所有交易所内的交易数据。
#### Analytics
* 分析数据可以认为是基于原始数据的衍生数据。
#### Alternative Data
## bars
* 为了让ML算法处理这些非结构化数据，需要把原始数据进行结构化。结构化的表的行，成为bars。
###  Standard Bars
#### Time Bars
* 时间序列的bars。Time bars是通过对数据做一定时间内的采样获取而来。包括：Timestamp,Volume-weighted average price, Open (i.e., first) price,Close (i.e., last) price,High price,Low price,Volume traded, etc.
* 从实际生产的角度来说，Time bars是尽量避免的的
#### Tick Bars
* 在Mandelbrot and Taylor’s 论文后，其他更多的研究表明在交易事件中利用sampling信息可以获取接近IID Normal的回报。
  当你在构建Tick Bars的时候，要特别注意异常值。
#### Volume Bars
#### Dollar Bars
### Information-Driven Bars，主要是研究一些微观架构
    Information-Driven Bars的目标是对新进入市场的“信息”做更频繁的采样。这里的信息指的是市场的microstructural sense。通过对微观结构的研究，可以发现提前发现标的物的价格不平衡情况的信号，从而做出决策
#### Tick Imbalance Bars
   一个Tick sequence：{(pt, vt)}t=1,…,T，pt是tick-t的价格，vt是tick-t的volume.定义Tick rule sequence：{bt}t=1,…,T
   bt = bt-1 if δpt=0, abs(δpt)/δpt else
   bt ∈ {-1, 1}， 即bt是一串{-1, 1 ... }的序列，只要下一个tick的价格和上一个一样，bt=0， 否则=1，所以，bt体现的是tick的价格是否发生了变化。 
#### Volume/Dollar Imbalance Bars
   volumn imbalance bars(VIBS), dollar imbalance bars(DIBS) 是tick imbalance bars 的扩展。我们希望在Volumn或者Dollar imbalances 偏离我们预期的时候，对他们进行采样。
#### Tick Runs Bars
    大Traders会sweep order book，使用iceberg orders,或者把一个parent order分成若干小order。所以监控overall volume 上面的buy操作是有意义的，然后对这些操作采样samples。
#### Volume/Dollar Runs Bars
## 2.4 DEALING WITH MULTI-PRODUCT SERIES
   说的是我们需要关注有特殊事件发生的products，这些事件，例如分红，分息，等等，会对正常的时间序列instruments造成本质的变化。
  后面主要讲的是如何把一篮子securites当成一个cash products进行建模，称之为"ETF trick"。目标是把一揽子复杂标的物转成一个cash product，融合了原来的一篮子securites收益。
### ETF Trick
交易期货价差(future spread)的问题是：价差特征可以被一系列动态变化的权重向量来描述.
因为权重动态变化，价差有可能在价格没有变化的情况下收敛。这个可能会导致model误认为是市场自动收敛的。第二，价差(spreads)有负数，以为很多model支持处理正数。一个解决办法就是引入一个时间序列能正确反应spread的价值。
考虑如下历史bars：

oi,t is the raw open price of instrument i = 1,…, I at bar t = 1,…, T.
pi,t is the raw close price of instrument i = 1,…, I at bar t = 1,…, T.
di,t is the carry, dividend, or coupon paid by instrument i at bar t. This variable can also be used to charge margin costs, or costs of funding.

$$
h_{i,t}= 
\begin{cases}
\frac{w_(i,t)K_t}{φ_i,t}\sum_{i = 1} ^I(w_i,t) \quad t\in B\\
h_i,t-1 \quad otherwise
\end{cases}
$$

### PCA Weights
  对weights进行PCA降维
  重新review一下推导向量{w_t}.考虑一个独立同分布的multivariate Gaussian process的向量，N*l大小

### Single Future Roll
  ETF tricks可以处理一张远期滚动合约。然而，处理单一远期合约的时候，一个同样并且更直接的方法是

## 2.5 Sampling features 特征采样