第二章-1 金融数据结构

 - Bar一般包含HLOC price. time 和volume.
 - 构造bar可以从两个维度来分类。
    - bar分割的量，如时间(T)、交易量(V)、交易额(D)
    - bar分割量的方法，如固定步长、找量的突变点(I)、找买量和或卖量的突变点(R)
 - 由以上两个维度排列组合成9个不同类型的bar. 分别是
    - TB,VB,DB：fixed T/V/D per Bar
    - TIB,VIB,DIB：imbalance points of price/V/D
    - TRB,VRB,DRB：imbalance points of max{buy,sell} of price/V/D
