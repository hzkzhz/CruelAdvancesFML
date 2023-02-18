# AFML: pp 63 - 64

4.5.1 Sequential Bootstrap

- 上一轮sample过的 $\phi^{(1)}=\{i\}$ ，这一轮被sample的概率调小一点，主要是调整uniqueness $u_{t,j}^{(2)}$ (第二轮，时间t，在feature j中)
    - $u_{t,j}^{(2)}=1_{t,j}(1+\sum_{k\in\varphi^{(1)}}1_{t,k})^{-1}$
        - 意思就是当前这个时刻在上一次被sample到了几个（如果一次sample有好几个feature的话，如果只sample一个feature就只有一个$1_{t,k}$）
        - Intuition就是如果跟上一轮的重合多，那现在就给它调小一点
    - $\bar{u}_j^{(2)}=(\sum_{t=1}^Tu_{t,j})/(\sum_{t=1}^{T}1_{t,j})^{-1}$
        - 这里其实很简单，分子就是这一个段（index是j）里每一个时刻的uniqueness值；分母是这个段里有多少时间
    - 每一段被sample到的概率就是normalize一下之后的值
        - $\delta_j^{(2)}=\bar{u}_j^{(2)}(\sum_{k=1}^I\bar{u}_k^{(2)})^{-1}$

