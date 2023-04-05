# TE: pp 77-78

##### 4.4.4 The risks of using standing limit orders

两种risk：

- execution uncertainty 下的单执行不了
- Ex-post regret
    - 下单被执行后觉得自己下的价格不够好
    - important cause: *adverse selection risk*
    - dealer（主要提供流动性的trader） 不喜欢和知道更多未来价格变动信息的trader交易

之后会讲细节：

- Ch11: extract limit order option values
- Ch12: bluffers
- Ch13: trade with better-informed traders
- Ch15: large traders pose as small traders

##### 4.4.5 Limit Order Represent Absent traders

- trader告诉broker在什么condition下会交易，broker就代替他们去monitor the broker，然后trader就可以去参与别的交易了

##### 5. Stop orders

- buy only after price rises to the stop price or sell only after price falls to the stop price
- 通常用来stop losses当prices move against their positions => stop loss orders
    - 可能交易的时候并没有按照stop price价格交易（比如价格跌太快了，sell的价格可能会更低）
    - 如果为了有确定的价格 => 买put option
