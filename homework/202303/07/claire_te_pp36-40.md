# TE: pp 36-40

##### 3.2.2.2 Settle Agents

- 从买家那里拿钱，从卖家那里拿securities
- clearing和settlement紧密联系
- 只做净结算（一方给一方差额的钱就行了）

##### 3.2.2.3 Clearinghouses

- 期货期权swap都有对应的清算所。
- 清算所owned by清算会员，清算会员才可以settle all trades
- 如果清算所会员没法settle a trade（通常由于破产），清算所会tax its other members to settle the trade!
- 因为⬆️所以对会员有margin等的要求

##### The Brazillian Straddle

- Straddle: 在两种不同类型的instruments中持有头寸
- Technically bankrupt的trader可能会增加头寸，给担保他们交易的公司更大风险（赚了可能逃过破产，亏了也就破产）=> 这种策略叫 *Brazilian straddle* （头寸 + 机票😂）
- 为了避免这个问题，清算会员要求trader经常报告他们的position，并且在价格大幅变动不利于trader的那一天内支付保证金，确定trader无法结算的时候禁止交易；签合约如果trader没报告问题的话 technically bankrupt的trader赚的任何利润都要分给清算公司

###### T+5 and Counting Down

- 1995.6之前都是T+5，后来是T+3，2005.6之后是T+1.
- 结算越快越好（不然很可能因为交易变动，一方不愿结算
- T+1 需要会员提前存点钱，足够第二天settle

###### Straight-Through Processing(STP)

- trading system提供自动的clearing和settlement process

- cheap, minimize the potential for errors

##### 3.2.2.4 Depositories and Custodians

- 代表客户持有现金和证券
- 最大的存款机构 DTC

##### 3.3 Trading Instruments

3.3.1 Real Assets

- 现货、知识产权、房地产、排污权 etc
- 交易的更多是贵金属、农作物之类的（fungible）
- 更关心price而不是quality

3.3.2 Financial Assets

- 略：equity, debt, MBS, CMO

- Stripping bonds:
    - 想要大量零息债券（多于available）=> 零息债券价格上涨超过coupon bond => 套利（买straight bonds，分离coupon，把coupon同一时间发的bundle起来，bundle和分离之后的principal（作为零息债券）分开卖
