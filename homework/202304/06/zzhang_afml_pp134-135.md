# AFML: pp 134 - 135

##### 9.4 Scoring and hyper-parameter tuning

- 当在investment strategy调参的时候推荐用`neg_log_loss` 
- 投资策略受益于high confidence 地预测正确的标签。 low confidence good prediction的收益不足以抵消high confidence bad prediction的损失。
    - accuracy 没法address这一点，但log-likelihood把这一点考虑进去了【但实际上我觉得用分类到k的概率耶能考虑到啊】

$$L[Y,P]=-\log(\Pr(Y|P)) = -1/N\sum_{n=0}^{N-1}\sum_{k=0}^{K-1}y_{n,k}\log p_{n,k}$$

- $p_{n,k}$：probability associated with prediction *n* of label k
- Y 是真实值

实际中应用sampled weighted cross-entropy

- correct label for the side, 
- probability for the position size, and 
- sample weight for the observation’s return/outcome.

