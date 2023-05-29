# TE: pp 245-250

#### Ch 11: Order Anticipators

- 三类：
    - front runners 收集其他trader打算的交易
    - sentiment-oriented technical traders 预测uninformed trader打算做的交易
    - squeezers 剥削其他必须做某个trade的trader
- 是parasitic trader，且并没有让price更加informative，反而使price更加volatile，market更加不有效
- 有时候可能是broker透露的order信息

##### 11.1 Front Runners

- 收集其他trader打算做的交易（broker针对客户相关的front run违法）

##### 11.1.1 Front Running Aggresive Traders

- demand liquidity，所以会有price impact
- front run 从 price impact中获利 （从brokerage那里拿到的和偷听得到的confidential 信息来front run是违法的）
- front-runner 拿走large trader们通过价格歧视的来的profit（通过让large trader pay 更多来获利）
- 多个front runner一起front-run会对价格产生更大的影响。front runner通常trade不怎么efficiently因为他们trade太快了。
- 下大单最后可能就选择block trader了，用统一价格成交

##### 11.1.2 Front Running Passive Traders

- passive trader提供流动性
- front run passive trader => 试图提取passive trader 订单的期权价值。
    - quote matcher
- quote matching: 尝试在耐心的大交易者面前（并与其站在同一边）进行交易
    - 如果价格对他们不利，通过与passive trader交易来限制他们的损失。 如果价格朝着有利于他们的方向发展，会在价格变化的最大范围内获利。
    - => penny jumping
- take liquidity that otherwise would have gone to the passive traders
- 需要考虑transaction cost
- 避免被front run: hide order，倾向于market order而不是limit order => 增加了transaction cost，降低了market transparency

