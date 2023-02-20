# AFML: pp 65-66

4.5.2 

`getIndMatrix(barIx, t1)` 函数

- `t1`: index是观察到的这个feature；value 是label被决定的时刻
- 相当于 bar 在 观察到的时间 ~ label决定的时间 内的都属于影响这个label的bar 
- 返回的矩阵：index是所有的bar index；column里的数值表示 `t1`里的第几行

`getAvgUniqueness(indM)`函数

- c: 算每个时刻有多少条数据（`t1`里有多少行包括了这个时刻）

`seqBootstrap(indM, sLength=None)` 函数

- `sLength` 表示要sample多少条数据
- `phi` 返回的是被sample到的数据（t1里的一行）
- `for i in indM` 返回的其实是columns
- `indM_=indM[phi+[i]]` 其实是在返回之前被sample过的+现上当前列的，试图去计算
    - $u_{t,j}^{(2)}=1_{t,j}(1+\sum_{k\in\varphi^{(1)}}1_{t,k})^{-1}$$
    - 不过这里$\varphi^{(1)}$ 它之前所有sample过的数据

4.5.3 例子略
