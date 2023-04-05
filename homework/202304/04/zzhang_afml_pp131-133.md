# AFML: pp 131 - 133

9.3 Randomized search cross-validation

- 除了grid search还可以sample each parameter from a distribution

9.3.1 Log-Uniform Distribution

- 一些参数要求：positive，非线性均匀变化（从0.01到1和从1到100效果差不多）

- => logarithm 是 uniform的

- $log(x)\sim U[log(a),log(b)]$

- $F[x]=\frac{\log x - \log a}{\log b - \log a}$

- $f(x)=\frac{1}{x\log b/a}$

    
