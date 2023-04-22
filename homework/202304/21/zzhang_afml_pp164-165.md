##### 12.4.1 Combinatorial Splits

- T个observations划分成N组，如果有k组作为test group，则总共分法有$\binom{N}{N-k}$，总共有$k\binom{N}{N-k}$ 个test observations（有可能重复）。所有 大小为 k 的testing sets on N，我们总共有 $\varphi[N,k]=k/N\binom{N}{N-k}$ 那么多条Path（没太懂）？
- 训练数据的比例$\theta=1-\frac{k}{N}$ 随着N变大而变大，而随着$k$变大而缩小
- 训练Path的数量随着$N$增大和$k\to N/2$都增大。
