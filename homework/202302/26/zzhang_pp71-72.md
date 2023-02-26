# AFML: pp 71-72

4.8 Class weights

- 有些class的sample很少（比如 liquidity crisis），所以挺有必要给不同的class assign不同的weight => 用 sklearn的时候设置一下weight就可以了

- `class_weight='balanced'` 会让所有class 以相同频率出现
- `class_weight='balanced_subsample'` 只对 in-bag bootstrapped samples 实行balance，而不是整个数据集  
