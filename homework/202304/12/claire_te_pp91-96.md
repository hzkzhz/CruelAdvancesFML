# TE: pp91-96

##### 5.2.3 Call Versus Continuous Trading Sessions

- call market的好处，固定时间交易某个instrument，较容易能够找到交易对手
- 一些国家把交易所模式从 call market rotation 改到了 continuous trading with opening calls.

##### 5.2.4 Trading Hours

- 有些交易所开盘时间会match别的开盘时间
    - NYSE: 9:30 am
    - CSE: 8:30 am 来match NYSE
    - Pacific Exchange: 6:30 am 来match NYSE
- FX traders的时间会比较不同
- 有些market支持 after-hours trading sessions 来吸引别的时区的clients或者让trader能够在regular trading session结束后还能调整仓位
- 有些交易所由lunch time，有些没有但是在lunch time的trading activity也会少很多

##### 5.3 Execution Systems

- 如何match buyers and sellers
- 主要有三种，quote-driven, order-driven, brokered

##### 5.3.1 Quote-driven Dealer Markets (dealer markets)

- dealer 参与每一笔交易，想要trade必须通过dealer。public trader之间没法直接交易
- 大部分sport betting market都是dealer market，bookies是dealer
    - bookies 需要努力balance the books，通常会和别的bookies来做offsetting bets，但非常costly，因为会被抽水
    - 如果book balance了，唯一的风险就是输的client付不起钱
- 有些dealer market，public trader也可以相互交易，但是broker提供了大部分流动性，比如NYSE
- dealer一般选择信任的trader交易，但不想和well-informed trader交易
- Interdealer brokers帮助dealers arrange trades among themselves
- 大部分bond, currency market和很多stock market都是quote-driven的
- 大部分dealer market都是通过informal networks of dealers，更structured dealer market则通过电子交易system，比如Nasdaq, London SE, eSpread gov bond trading system.

##### 5.3.2 Order-driven Markets

- buyer和seller直接交易，不通过dealer
- *order precedence rules*
- *trade pricing rules*
- 大部分是*auction market* 
    - *price discovery process* 
    - *single-price auction* 一个价格安排所有trades following a market call
    - *continuous two-sided auctions* 买卖双发持续出价
    - *crossing network* 匹配orders 以其他市场的价格
    - *oral auction* 在交易所面对面商量 => *open-outcry auction*
    - *rule-based order-matching system* 市场按照一定规则自动匹配 => 电子交易
- dealer可以交易，可能也提供了绝大多数流动性，但dealer不能够选择clients，要求他们和任何能够接受他们offer的人交易
- Order-driven market非常常见
    - 所有由electronic auction和open-outcry auction的都是
    - 所有major futures exchanges, 大部分stock and options exchanges，以及很多brokerage 和ECN构造的trading system
    - Gov 通常也在order-driven market issue最新的debt securities

##### 5.3.3 Brokered Markets

- broker来match，特征就是：broker去寻找liquidity
- 通常非常illiquid，dealer不愿意交易
- 在这儿的通常有两类trader：
    - concealed traders：想交易，但不想那个在public公开这个order，直到broker提供合适的交易机会才愿意交易
    - latent traders：在broker他们告诉有这个交易之前没想着交易
- 当交易的东西比较unique的时候比较常见，比如large blocks of stocks and bonds，房地产，markets for going business concerns

##### 5.3.4 Hybrid Markets

- 混合了上面三种的特征
- 尽管NYSE 是order-driven的，它还是需要specialist dealers来提供流动性如果别人不愿意的话，所以它也有一些quote-driven的特征
- 尽管Nasdaq是quote-driven的，它还是需要dealer去处理一些public limit orders，所以它也有一些order-driven的特征
- 因为broker有时候需要arrange large block trades在这两个交易所中，所以他们也有brokered markets的特征

