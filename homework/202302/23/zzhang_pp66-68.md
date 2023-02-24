# AFML: pp 66-68

#### 4.5.4 Monte Carlo Experiments

**Generating a random T1 Series (4.7)**

- number of observations：`numObs`

- Each observation 开始的bar:  $\sim U[0,\text{numBars}]$
- Each observation包含的bar个数 $\sim U[0, \text{maxH}]$

**Uniqueness from standard and sequential bootstraps (4.8)**

- 生成了两个average uniqueness `stdU`（根据随机sample的），`seqU`（根据顺序抽样的，就是考虑那个尽可能不overlap的抽样算法）

**Multi-threaded Monte Carlo (4.9)**

- 主要就是用了多线程跑4.8的function
- 结果就是顺序抽样（考虑overlap的）比随机抽样的uniqueness要高一点 => 主要目的就是让抽到的observations尽可能IID，所以顺序抽样更好点
