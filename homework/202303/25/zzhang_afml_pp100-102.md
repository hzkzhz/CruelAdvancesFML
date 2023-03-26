# AFML: pp 100-102

6.7 Bagging for Scalability

- 当数据量变多的时候，SVM fit model需要很多时间
- 可以用bagging的方法，先 fit 一个base SVM model
    - 设定比较低的`max_iter`
    - 提高converge的tolerance level: `tol`
- bagging 可以并行的训练很多estimator，通过提高estimator数量降低variance

