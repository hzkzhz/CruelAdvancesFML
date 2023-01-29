# Financial Machine Learning as a Distinct Subject
## 1.2 The Main Reason Financial Machine Learning Projects Usually Fail
### 1.2.1 The Sisyphus Paradigm

Hire 50 discretionary portfolio managers and make the portfolio correlation as low as possible, if one of them makes money, it covers all the costs.

Problems:

1. Look great in an overfit backtest
2. Standard factor investing is overcrowded

### 1.2.2 The Meta-Strategy Paradigm
Instead of making a single car each person, try to build a modern factory.


## 1.3 Book Structure
### 1.3.1 Structure by Production Chain
Macroscopic alphas are hard to find, but microscopic alphas are abundant.

#### 1.3.1.1 Data Curator
- Data collecting, cleaning, indexing, storing, adjusting and delivering all data to the production chain
- Data handlers to understand data
- Based on differenct asset classes

#### 1.3.1.2 Feature Analysts
Transforming raw data into informative signals

#### 1.3.1.3 Strategiests
Trnsforming informative features into actual investment algorithms.


#### 1.3.1.4 Backtesters
Assess the profitability of an investment strategy
1. historical path
2. Alterative scenarios
Overfitting must be taken into account

#### 1.3.1.5 Deployment Team
Algotirhm specialists and hardcore mathematical programmers.

- process schedulers
- automation servers(Jenkins)
- vectorization
- multithreading
- multiprocessing
- graphics process unit(GPU-NVIDIA)
- distributed computing(Hadoop)
- high-performance computing(Slurm)
- parallel computing techniques


#### 1.3.1.6 Porfolio Oversight
After a strategy is deployed, the lifecycle:
1. Embargo: run on data after the end of backtest.
2. Paper tradng: on live, real-time feed.
3. Graduation: manage a real position.
4. Re-allocation: based on production performance, re-assess the allocation.
5. Decommision: discontinue when a strategy is below expectation.