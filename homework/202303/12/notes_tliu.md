# notes

我发现我可能暂时只适合读每一章的引言。我就把前面的看看剩下的可以下一轮再看。

fractionally differentiated features

学到了一个词：arbitrage 套利。由于套利的存在，金融数据序列的信噪比非常的低。而一些连续的数据比如价格序列稍微好一点，return 序列比较糟糕，为了存储着想，我们定期要清理数据。

不是非常理解，感觉内存不应该是非常充足的吗？这里的存储不足到底指的是谁的存储不足了呢？

作者这里提到了一个 dilemma，return series 是stationary的，但是也是memory less 的。price 是 non stationary，但是 memory ful 的。

作者提到：监督学习非常需要 stationary，因为监督学习就是把一些没有标签的observation映射到有标签的数据上。stationary是一个必要条件不是一个充分条件，它并不代表一定这个模型预测能力就强。