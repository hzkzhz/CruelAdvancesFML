# TE: pp 118-120

##### 6.2.2 The Matching Procedure

- 按照ranking来match
- 先match最高优先级的buy和sell

##### 6.2.3 Trade Pricing Rules

- Single price auctions use the *uniform pricing rule.* 
- Continuous two-sided auctions and a few call markets use the *discriminatory pricing rule.* 
- Crossing networks use the *derivative pricing rule.*

##### 6.3 The uniform pricing rule and single price auction

- 大部分open session都是single price auction
- 所有trade都有以market-clearing price成交
- The last match that leads to a feasible trade determines the clearing price. 如果buy price比这个高也会按照clearing price成交，如果sell price比这个低也会以clearing price成交
- 通常这个price是相同的。但如果价格不match，而且buy的价格比seller offer的高，market会选择[offer price, bid price] 中的一个价格成交（屈居于market rule）
