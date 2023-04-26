# TE: pp 112-116

### Ch 6 Order-driven markets

- 所有订单驱动的市场都使用订单优先(order precedence)规则来匹配买家和卖家，并使用交易定价(trading pricing)规则来为最终交易定价。
- 不同市场的trading rules不同

##### 6.1 Oral Auctions

- 最大的口头竞价市场是美国政府多头国债期货市场。最小的口头拍卖可能只包括两个trader。
- 买家和卖家经常轮流出价和报价，直到他们就交易价格和数量达成一致。
- 第一条规则是公开喊价规则：确保所有交易者都能公平地参与市场。任何交易者都可以接受另一交易者的出价或报价，即使他或她并未积极与该交易者谈判。第一个接受买价或卖价的交易者通常会开始交易。
- 第二条规则是交易员公开表示接受，以便所有交易员都知道他们安排的交易。

##### 6.1.1 Order Precedence Rules

- 主要的顺序优先规则始终是*price priority*。次要优先规则取决于市场。 期货市场使用*time precedence*。 美国证券交易所使用**public order precedence* *，然后是时间优先。
    - *price precedence*: self-enforcing的规则，因为诚实的交易者自然会寻找最好的价格，交易所不必采用特殊程序来执行它
    - *time precedence*: 在口头拍卖市场中，出价和报价通常只在一瞬间有效，交易者通过尽可能频繁地重复他们的报价来保持他们的优先级，以表明他们仍然对交易感兴趣。
        - 鼓励交易者积极提高价格。Rewards **aggressive traders** by giving them the exclusive right to trade first at the improved price
        - 仅当最小价格增量不是很小的时候，时间优先才有意义！如果 tick 太小，它会通过削弱时间优先规则来减少价格竞争。 如果tick太大，交易者会因为费用而不愿提高价格。
        - 价格变动大小的减少降低了时间优先权的价值，会大大减少displayed order sizes.
        - 当有人不正当地试图以相同价格出价或报价时，拥有时间优先权的交易者必须为其辩护 => oral market里就喊出来 that's my bid.
    - *public order precedence*: 
        - 证券交易所禁止其成员在愿意以相同价格交易的公开交易员(public trader)之前进行交易，即使该成员有时间优先权，以此削弱场内交易者的信息优势。
        - 但随着最小价格增量的减小，该条规则被大大削弱

##### 6.1.2 The Trade Pricing Rules

- Every trade takes place at the price proposed by the trader whose bid or offer is accepted.
- *discriminatory pricing rule* 歧视性定价规则：大型trader会区分最愿意交易的trader和只愿意以较低价格交易的trader，从前者获得最好的价格，从后者获得最差的价格，以降低了他们的交易成本，因为最愿意交易的交易者如果知道完整的订单规模，就不会提供这么好的价格。

##### 6.1.3 Trading Floors

- 略

##### 6.2 Rule-based order-maching systems

- 交易者仅通过提交和取消订单来相互协商。 大多数系统只接受限价订单。
- 如果市场是call market，则市场在call前收集订单。如果是连续交易市场，其交易系统会尝试在新订单到达时安排交易。
- 首先使用订单优先规则match订单。 然后他们决定哪些match可以trade

##### 6.2.1 Order Precedence Rules

- 下一个note
