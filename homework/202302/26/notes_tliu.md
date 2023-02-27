# notes

现在我们考虑如何加入风险的考量，即止损点和止盈点。

在这里用一段代码提前算好了动态的阈值：exponentially weighted moving standard deviation

```python
def getDailyVol(close, span0 = 100):

    # daily vol, reindexed to close 
    df0=close.index.searchsorted(close.index-pd.Timedelta(days=1))

    df0=df0[df0>0]

    df0=pd.Series(close.index[df0–1], index=close.index[close.shape[0]-df0.shape[0]:])

    df0=close.loc[df0.index]/close.loc[df0.values].values-1 # daily returns 
    df0=df0.ewm(span=span0).std() 
    return df0
```

这里 searchsorted 的作用是在一个已经排序好的 pandas 序列中搜索特定的值的下标。一开始我们在 close 的 index 中搜索 close.index 减掉一个值 pd.Timedelta(days=1)。

这个 pd Timedelta 就是返回一个时间 duration，所以就是每个 index 都减一天的意思。

后续的操作看起来好像只是为了实现一个：
    （当前价格 / 一天前价格） - 1
的效果。不知道为什么他要这样写？

最后使用 pd.Series.ewm().std() 计算出exponential weighted mean 的 standard deviation。