# notes

如果从 tick 数据抽样到 bar 数据，大方向上有两种方法：


标准法：等时抽样、等笔抽样、等量抽样、等额抽样


信息驱动法：

    Imbalance 抽样，满足条件

    |Imbalance| ≥ Expected Imbalance


    Runs 抽样，满足条件

    |Run| ≥ Expected Run


实操起来坑很多：
数据量太大，运行时间太长。


画出来的图和 Prado 书上不太一样 (看不出 dollar bar 最稳定)，光看图不行，还需要用具体的统计指标来证明 dollar bar 最稳定。


抽样 IB 和 RB 需要超参数，这些参数怎么改没有一个明确的规则，我也是慢慢试出来的，而且发现每次抽样的结果对超参数非常敏感。

