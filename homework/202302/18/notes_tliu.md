# notes

回归打卡

之前我们都考虑的是单一 product，现在比如要考虑一揽子股票的时候，a basket，之前的方法就可能会失效，比如这一揽子会 rebalanced，或者是 weights 会改变等。

把 multiproduct 处理成 single product 可以让我们之前的代码不用改也能直接用，提高复用性。

接下来介绍 ETF trick：

写了一个看的不是很懂的公式，计算了若干变量：raw open price，raw close price，看起来单位都是 point。USD value of one point，单位是美元每点。交易量；carry，dividend，coupon，这些看起来可能是分红什么的。

然后计算出了 h for holdings； delta for change of market value between t-1 and t for instrment i. K for investment value.