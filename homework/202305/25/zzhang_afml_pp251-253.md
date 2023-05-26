# AFML: pp 251 - 253

#### 17.4 Explosiveness Tests

- test 单个bubble 或者 多个bubble

##### 17.4.1 Chow-Type Dickey-Fuller Test

- 假设序列一开始是random walk，$\tau^* T$ 之后explosive

- 相当于 test $\Delta y_t = \delta y_{t-1} D_t[\tau^*] + \epsilon_t$ 里 $\delta = 0$ (H_0)。这里 $D_t[\tau^*]$ 是个binary 用来指示是否超过 $\tau^* T$. 
    - H_0: $\delta = 0$ (One-sided), H_a: $\delta > 1$ （感觉应该是 $\delta > 0$ 才对吧）

- $DFC_{\tau^*}=\hat{\delta}/\hat{\sigma}_\delta$
- 缺陷：
    - $\tau^*$ 不知道 => 试一个范围内的所有$\tau^*$ 
        - $SDFC = \sup_{\tau^*\in[\tau_0,1-\tau_0]}DFC_{\tau^*}$
    - 假设只有一个break date => 后面的方法解决了这个问题，可以测多个regime啦

##### 17.4.2 Supremum Augmented Dickey-Fuller

$$\Delta y_t = \alpha + \beta y_{t-1} + \sum_{l=1}^L \gamma_l\Delta y_{t-l} + \epsilon_t$$

- H_0: $\beta \le 0$, H_a: $\beta > 0$
- $SADF_t=\sup_{t_0\in[1-t-\tau]}ADF_{t_0,t}=\sup_{t_0\in[1,t-\tau]} \frac{\hat{\beta}_{t_0,t}}{\hat{\sigma}_{\beta_{t_0,t}}}$
    - beta 是从 t0 - t 预测回归得到的，tau 是最短的sample长度
- 相当于遍历了所有region吧
