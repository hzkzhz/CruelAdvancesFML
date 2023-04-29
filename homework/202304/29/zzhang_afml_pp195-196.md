# AFML: pp 195-196

### Ch 14: Backtest Statistics

##### 14.1 motivation

- 主要介绍比较performance的metrics

##### 14.2 Types of Backtest Statistics

- 回测统计数据应该帮助我们发现战略中可能存在问题的方面
    - 例如大量不对称风险或low capacity。 
    - 它们可以分为general characteristics、performances、runs/drawdowns、implementation shortfall、return/risk efficiency、classification scores和归因(attribution)。

##### 14.3 General Characteristics 

- time range：回测的开始时间和结束时间，是否足够长包含足够多的regime
- average AUM：管理资产的平均dollar value
- capacity：能够到达目标risk-adjusted performance的最高AUM
- Leverage：借多少钱，如果有leverage，要考虑相关的cost，
    - measure方法：average dollar position 除以average AUM
- Maximum dollar position size: 看是否会超过AUM，还是期望能够close to average AUM，
    - 说明他们不rely on exterme events

- Ratio of longs：如果是long-short market neutral的，这个值理想情况下close to 0.5
- Frequency of bets：number of bets per year in the backtest。
    - 单边的连续positions被认为是一次bets。当position flattened或者flipped to另一边，则认为是这次bet结束
    - bet次数通常比trade少，用trade次数会高估这个策略发现的独立的机会
- Average holding period: 一个bet hold的平均时间。
    - Short holding period会限制capacity of the strategy
    - 和frequency of bets相关但不同
- annualized turnover: average dollar amount traded per year 处以 average annual AUM

- correlation to underlying：策略的return和underlying investment universe return 的相关性。如果相关性接近1或-1，说明只是单纯long-short
