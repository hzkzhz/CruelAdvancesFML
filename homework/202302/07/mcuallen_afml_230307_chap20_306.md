[toc]

# atom vs molecule
When preparing jobs for parallelization, it is useful to distinguish between atoms and molecules.
当准备并行化的工作时，区分原子和分子是很有用的。
原子任务不可分割，而分子任务可以分割为更小的任务。并行化是发生在分子级别上的。

# wrapper
It would be a mistake to write a parallelization wrapper for each multiprocessed function. Instead, we should develop a library that can parallelize unknown functions,
regardless of their arguments and output structure. That is the goal of a multiprocessing engine. 
为每个多进程函数编写并行化包装器是错误的。相反，我们应该开发一个库，可以并行化未知的函数，而不管它们的参数和输出结构如何。这就是多进程引擎的目标。

# sklearn
Python has a parallelization library called multiprocessing. This library is the basis for multiprocessing engines such as joblib,2 which is the engine used by many sklearn algorithms
python有一个并行化库叫做multiprocessing。这个库是许多sklearn算法使用的引擎joblib的基础。