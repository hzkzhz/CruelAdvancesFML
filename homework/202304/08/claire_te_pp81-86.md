# TE: pp 81-86

##### 4.7 Tick-sensitive orders

- *uptick* 当前价格比上一个价格高; *downtick*, *zero tick*
    - *zero downtick* 上一个不同的价格比现在高；*zero uptick*
- 根据上一个价格变动下的order => *tick-sensitive order*
    - *buy downtick order*: 只有*downtick*和*zero downtick* price会成交 => trade price比上一个不同的价格低; 
    - *sell uptick order*: 类似. trade price higher than the last different price
- Broker 收到了后就会看condition有没有符合，符合就交易，不符合就等到有符合了再交易

##### 4.7.1 Tick-sensitive order properties

- 确保没有market impact 
    - 没有demand liquidity还是提供了流动性（在别人想交易的时候交易）
    - 相当于动态的不停下单（买单：比当前价格低一个tick）
- 适合想要让他们的limit orders close to the market when prices move away from them.
- 当最小价格变动(*minimum price increment*, *tick*) 比较大的时候，这种单比较attractive

##### 4.8 Market-not-held orders

- orders that brokers do not need to fill immediately
- 表明即使 they will not hold their brokers accountable for failing to trade
- tradermost often用这个order，当他们给了broker一个large order to fill。
- Most commonly会给在exchange floor工作的broker 或者 electronic order desk

##### 4.9 Validity and expiration instructions

- 表明什么时候他们的order valid什么时候expire
- 对standing limit order和stop order更重要
- 最常见的就是day order 交易日当天有效
- Good-till cancel (GTC) ：直到trader明确cancel它一直有效
    - 为了防止trader忘记，broker每个月月底都会公布他们unfilled GTC orders
- Immediate-or-cancel orders (IOC): 只有当他present to market的时候有效
    - 当trader不想给trading options
    - 其他名字：*fill-or-kill orders(FOK)*, *good-on-sight order*
- *Good-after orders*: good only after some specified date。很少见，除非你是个很重要的客户，不然broker不会接这种order
- *Market-on-open orders*: 只有在刚开市集中竞价的时候才会执行，比较容易执行，一般broker收的commission费用低一点
- *Market-on-close orders*：在闭市前执行，broker不保证order会被fill，trader想保证执行的话，可以buy them from dealer-broker by paying hier commissions。对mutual fund比较attractive，因为要去算NAV。

##### 4.10 Quantity Instructions

- 表明他们的broker是否可以用多个trade来fill 他们的大单
- 常见的是 *all-or-none*（一次交易完）和 *minimum-or-none*（可以多次交易，但每次的交易量要大于等于minimum acceptable quantity）

##### 4.11 Other order instructions

##### 4.11.1 Spread Orders

- 当他们想同时买一个instrument卖另一个instrument
- 可以是market order也可以是limit order
- limit order：设置limit for the 两个价格之间的差值（premium），premium给buyer还是seller取决于你更想买还是更想卖

##### 4.11.2 Display Instructions

- 制定broker怎么display那些还没有被fill的standing limit orders
- 一般是show no more than some maximum quantity 不要展现得太多，怕market move away from them
- 没有完全显示（放到market上）的order：*undisclosed order*, *hidden order*, *reserve order*, *iceberg order*
- 一些电子交易所允许提交undisclosed limit order。其他想知道他们full size的方法只能提交 large marketable orders with fill-or-kill instructions attached.

##### 4.11.3 Substitution Orders

- invest or divest a specified amount of money by trading any of several securities
- broker一般根据哪个securities有更好的价格来决定交易什么

##### 4.11.4 Special Settlement Instructions

- *cash settlement*: 一般交易员在最后一刻决定，他们希望在投票或分配之前成为记录在案的股东。
- trader在pursue dividend capture strategies时也会使用特殊的结算指令。
- 一般不能简单地demand这种order，而是negotiate for it。broker一般会要更高的fee。

