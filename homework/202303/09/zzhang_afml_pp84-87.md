# AFML: pp 84 - 87

#### 5.6 Stationary with maximum memory perservation

- 用固定window的那种weight衰减方式，可以找到一个最小的$d^*$使得$\{\tilde{X}_t\}_{t=l^*,\cdots,T}$ stationary。
    - $d^*$ 量化了让这个序列stationary的memory量
    - 如果它已经平稳了，$d^*=0$
    - 如果它有单位根，$d^* < 1$
    - 如果它有explosive behaviour，$d^* > 1$
- 如果$0<d^*\ll 1$ （midly non-stationary），用full integer differentiation 会导致预测能力消失
    - differentiation之后的序列和原始的序列相关性过了$d^*$ 之后急剧下降
- 用$d=1$ 会导致over-differentiation

