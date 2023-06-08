# AFML: pp 303-316

##### 20.2 Vectorization Example

- 把for loop 换成一些matrix multiplication
- 实用：`itertools.product(it1,...itN,repeat=1)` 计算笛卡尔积，`zip(it1,...,itN)` 并行从输入的各个可迭代对象中获取元素，产出由 *N* 个元素组成 的元组，只要有一个可迭代的对象到头了，就默默地停止

##### 20.3 Single-Thread vs. Multithreading vs Multiprocessing

- GIL => single thread write
- 用multiprocessing => 比较难share object，划分成各个部分给processor去做

##### 20.4 Atoms and Molecules

- Atoms: 单个任务，Molecules：顺序执行的多个任务（单线程，有一个call back function）

##### 20.4.1 Linear Partition

- 线性划分，涉及任务balance

##### 20.4.2 Two-Nested Loops Partitions

- 如何划分一个lower triangular matrix的row，使划分出的任务balance

##### 20.5 Multiprocessing Engines

##### 20.5.1 Preparing the Jobs

- `mpPandasObj` 的参数：
    - `func` callback function，并行执行的function
    - `pdObj` 一个元组包含：传入func的molecules的参数名字；molecules包含的tasks
    - `numThreads` 如名字
    - `mpBatches`: number of jobs per core：如果比一大，说明molecules比core数多 => 可以多写一点这个，把molecules弄小点，比较容易分均匀
    - `linMols`: 判断partition是linear的还是double-nested的
    - `kargs`: func 用的keyword参数

##### 20.5.2 Asynchronous Calls

- 介绍了两个function
- `processJobs(jobs, task=None, numThreads=24)`
    - `jobs` 是个list，包含`func` callback，task 只是callback的名字
- `reportProgress(jobNum, numJobs, time0, task)` 
    - 打印运行过程数据

##### 20.5.3 Unwrapping the Callback

- 把jobs 这个list of functions给wrap出来

##### 20.5.4 Pickle/Unpickle Objects

- 必须要pickle methods才能assign给不同的processors
- `copy_reg.pickle(...)` 其实好像不用？

##### 20.5.5 Output Reduction

- 输出如何边输出边合并，而不是等所有都输出了再合并

##### 20.6 Multiprocessing Example

- 划分矩阵做矩阵乘法
