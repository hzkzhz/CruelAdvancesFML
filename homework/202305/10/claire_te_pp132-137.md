# TE: pp 132-137

##### 6.5 The derivative pricing rule and crossing networks

- crossing network 是唯一一个不是auction market的order-driven market
    - 从别的market那里拿相同的产品的价格 rossing price
    - 它用derivative pricing rule定价
    - 例子：NYSE after-hour trading session I，POSIT
    - 都是call market
- POSIT：在正常交易时间内每天八次cross股票
    - 在每次call后的七分钟内随机选择一个时间来assign crossing price。届时，POSIT 会计算每只股票在一级市场的出价和要价的平均值，并将该价格用作clearing price
    - 交易者使用 POSIT 是因为它让他们有机会在价差的中点完成他们的订单，而不会受到任何价格影响。
- 通常crossing price不会让两边都成交完，没被成交完的trader会在别的market submit order
- crossing不会对market price造成立刻的影响
- 三大主要的crossing network都不会display order imbalance之类的信息
- 很多 brokerages 试图在转发到交易所之前直接 cross 他们客户的单子

###### Informed trading in crossing network

-  因为NYSE after-hours trading sesssion 1 会用收盘价来作为crossing price，所以after-hour有影响股价的新闻的时候，crossing market的买卖单数就会不平衡 => 如果有重大after-hour events的时候 crossing network会拒绝为这些stock cross。

##### 6.5.1-6.5.2

- *stale price*
    - The stale price problem is an **adverse selection** problem. 
    -  The well-informed traders select the side of the market on which to trade to the disadvantage of their uninformed counterparts.
- *manipulated price*
    - 只要交易者同意以未来其他地方确定的价格进行交易，就存在价格操纵的可能性。如果双方都试图这样做，他们的努力可能会抵消.
    - 比如说，相信他们会在 POSIT 买入的trader有动力在一级市场下卖单以降低那里的价格，从而降低 POSIT 交叉价格。POSIT 在通话后七分钟内随机选择其交叉价格。 因此，潜在的操纵者必须在七分钟内压低价格。此过程通过增加操纵者必须提交的订单数量来增加操纵成本 => 更容易抓
    - 另一个例子是，现金结算的期货和期权合约的最终结算价格源自其标的工具的现金价格。 因此，当这些合约到期时，这些价格有时会受到操纵。为了防止操纵，一些现金结算的合约规定，当市场价值出现错误时，交易所可以选择最终结算价格来代表公允价值。
