# AFML: pp 269 - 271

##### 18.5 Encoding Schemes

- 因为fractionally differentiated series通常含有memory所以还是要encode一下

##### 18.5.1 Binary Encoding

- 1 if r_t >0, 0 if r_t < 0, remove r_t = 0
- tick data (intraday) 通常 heteroscedasiticity 所以只用sign，就丢了很多信息
- 可以sample subordinated stochastic process 比如 trade bars和volume bars
- 然后就可以regularize the distribution of |r_t|

##### 18.5.2 Quantile Encoding

- 给 r_t 一个有关它处在的quantile的code
- quantile边界用in-sample period 决定
- in-sample的时候：每个code assign的observation number应该差不多

##### 18.5.3 Sigma Encoding

- code 0: [ min{r}, min{r} + sigma]
- code 1: [ min{r} + sigma, min{r} + 2 * sigma]
- 总共 ceil[max{r} - min{r} / sigma] 个code

##### 18.6 Entropy of a Gaussian Process

- IID normal random process的entropy是 $H=1/2\log[2\pi e\sigma^2]$
- 可以给一个benchmark用来选择 estimator, message length, encoding 的选择
- Entropy-mplied volatility estimate $\sigma_H=(e^{H}-1/2)/\sqrt{2\pi}$

