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
* 时间序列的bars。包括：Timestamp,Volume-weighted average price, Open (i.e., first) price,Close (i.e., last) price,High price,Low price,Volume traded, etc.
#### Tick Bars
#### Volume Bars
#### Dollar Bars



