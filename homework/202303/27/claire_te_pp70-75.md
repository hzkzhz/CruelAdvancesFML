# TE: pp 70-75

##### 4.2 Some Important Terms

-  *bid*, *offer*, *quote*
-  *frim* price, *soft* price
    - *firm*: 打算就按照这个价格交易
    - *soft*: offer这个价格的trader可以在交易前改
-  *best bid*, *best offer* == *market bid*, *market offer*
    - *market quotation*: *{best bid, best offer}* 经常被叫做BBO
    - NBBO: national BBO (US)
-  *bid/ask spread*: *inside spread*, *touch*, *vigorish*(in sports betting markets)
-  *offer liquidity* 先给价格的那个？
-  *day limit order*
-  *standing order* 还没被fill的
-  *immediacy*: 想要马上成交 one of dimension of liquidity
-  *liquid* market: 没有significant adverse-effect on price
    - 表现：很多standing orders, spread小

-  *agency order*（帮客户下的）,*propriety orders*（自己账户的）
    - 很多market，agency orders有优先权
-  让broker下单的时候
    - 状态*pending* ：broker还没有confirm
    - 状态*working*: order下了还没被fill.

##### 4.3 Market Orders

- 小单立即成交 
- demand liquidity

##### 4.3.1 Market Orders Pay the spread

- Market order traders *pay the bid/ask spread.*
- 立即成交的买/卖单，付一半的spread（best estimate of value是bid-ask中间值）

##### 4.3.2 Price Improvement

- 比market bid/ask更高/低的bid/ask价格 => 缩小spread
    - 当spread很大且incoming market order很小的时候容易发生

##### 4.3.3 Market Impact

- When traders move prices to fill their orders, they have market impact
- 通常是交易大订单的最重要成本
- market impact取决于liquidity available in the market

##### 4.3.4 Execution Price Uncertainty

- 由于市场状况可能会迅速变化，因此使用市价单的交易者可能会以比预期更差的价格进行交易。
- 原因：在提交订单和执行订单之间可能发生的报价变化；执行大订单可能需要的不可预测的price concession
- 担心uncertainty可以用limit order

##### 4.4 Limit Orders

- 名词解释略：*limit order book*, *limit price*, *aggresively priced*

##### 4.4.1 Limit Price Placement

- *marketable limit order*: submit之后马上可以成交的
- *at the market*, *make the market*, *make a new market*
- *in the market*
- *behind the market*, *away from the market*

##### 4.4.2 Standing Limit Orders are Trading Options that offer liquidity

- 限价卖出单是一种看涨期权，可以让其他交易者在他们想买的时候有机会买进。
- 买入限价单同样是看跌期权，让其他交易者有机会在他们想卖出时卖出
- standling limit order 是期权，但不是期权合约
    - 期权合约是一种以指定价格交易工具的期权，writer将其出售给另一位trader。 无论买方最终是否行使期权，买方都会向卖方支付premium。 相反，write standing limit order 的trader不会将其卖给其他trader。 相反，他们自由地将option grant 给市场。
- standing limit order的期权价值是订单对其他交易者的价值。 
- standing limit order期权价值取决于limit price、, how long the orders will stand, 以及 price volatility.
    - 最重要的是limit price，好的价格交易的越快
    - 长期可用的订单允许交易者推迟他们的交易决定。 当出现这样的选择时，交易者喜欢在承诺交易之前等待，看看会发生什么。如果价格上涨，trader将尝试从限价卖单中买入，他们将忽略限价买单。如果价格下跌，trader就会尝试卖出现价买单，而忽略限价卖单。
        - 当价格大幅变化时，这些交易将是最有利可图的。 因为价值在长间隔内的变化比在短间隔内的变化更多，所以当交易者预计它们将长期可用而不是短时间内可用时，限价单交易期权更有价值。
        - Traders cannot wait too long to trade with valuable limit orders。接近市场的限价订单对于想要立即交易的交易者来说很有价值，但对于想要在决定交易之前等待并看看会发生什么的交易者来说价值不大。
    - 限价单期权在波动的市场中很有价值，因为波动性增加了使用限价单执行获利交易的可能性。
        - 能够在其他trader取消订单之前快速执行限价订单的trader，在波动的市场中更看重限价订单，相比在稳定的市场中
        - 由于trader不喜欢放弃期权价值，他们经常在市场波动时将限价订单放置在远离市场的地方，以降低他们的期权价值。 因此，**买卖价差在波动的市场中往往很宽**。
