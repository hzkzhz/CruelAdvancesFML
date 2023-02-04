# AFML: pp 45-55

3.4 The triple-barrier method

- 2个horizontal barriers: dynamic function of estimated volatility
    - profit- taking：超过一定profit就打label
    - stop-loss: 超过一定loss就打label
- 1个vertical barrier
    - expiration limit 超过一定bar就停止，label 0 或者按PnL正负打

3.5 learning side and size（Model-1）

介绍了几个函数（主要是打side的label)：

- `getEvents(...)`
    - 返回碰到第一个barrier的时间
- `getBins(...)`
    - 给找到的event打label：{-1,0,1}

3.6 meta-labeling （Model-2）

主要打是否bet的label（买/卖作为输入）

- 更新过的`getBins(...)`:  只返回{1,0} 意味着 take the bet 或者pass

3.7 how to use meta-labeling

- 只是为了filter out 一些被Model-1 认定为可以bet的机会，降低 false positive率
- 预测sizing很重要
- 用meta-labelling可以给ML黑箱上加点经济学相关的white box

3.8 the quantamental way

- meta-labeling layer 可以加在任何primary model上

3.9 dropping unnecessary labels

- 太imbalanced dataset 会影响classifier，可以丢掉一些class（除非只剩下2个class）
