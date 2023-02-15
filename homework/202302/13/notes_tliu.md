# notes

这里引入了 VIBs 和 DIBs 定义就是把 tick 换成了 volume 和 dollar 这样子。

然后 T*-contiguous 的定义也是一样的。

然后这些按照 tick 来划分的东西都会面临之前提到的问题，就是 large trader 可能会把一笔单子分拆成好多笔，然后会有一些其他的操作：iceberg orders 等。

所以我们可以去监控 buy sequence。我没有理解为什么监控 buy 单边就行。

剩下的操作和之前还是一样，定义 thetaT，然后定义 T*-contiguous。

总结来看，run bar 和 imbalance bar 的区别就是一个考虑总和，一个考虑某边的最大值。

使用类似的方法也可以弄出来 VRB DRB。

