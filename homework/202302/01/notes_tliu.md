# notes

之前介绍了如何生成连续的，齐次（emm不知道怎么翻译，可能要叫统一的？一致的？），结构化的数据集。现在我们就可以把ML算法直接用上去了，但是效果肯定不好，因为一般的 ML 算法不会 scale 样本的大小等等。我们需要如何 sampling 采样一些 bars

1. sampling for reduction
2. event based sampling

接下来我们要学习的是 labeling 使得我们可以搞一些监督学习