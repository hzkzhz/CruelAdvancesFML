# 第三章2-labeling
 - 所谓meta labeling 分成两步，第一步，做一个两类分类器，把recall做高，牺牲伪阳率，在ROC曲线上找分割门限
 - 由此得到prediction. 然后把prediction作为一个维度加入到原始的训练样本X_train中。比如原始x_train为（N,m）. 加入prediction后，变为(N,m+1).然后原始的y_train和prediction做“与”运算，结果作为新的y_train. 然后用新的x_train和y_train训练模型，ROC曲线可以大幅向左侧移动
 - 其中的原理可能是如此处理后，在第一个分类器中的伪阳样本增加了新的信息，与真阳和真阴样本有了区分，从而改进了模型
