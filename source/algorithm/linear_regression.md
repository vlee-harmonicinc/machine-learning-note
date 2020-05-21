# Linear Regression
see also:
[wiki/Linear_regression](https://en.wikipedia.org/wiki/Linear_regression)
Target: Finding the best fit line/curve to data
## OLS - Ordinary Least Square
based on matrix/ vector formulation
```math
\newcommand{\vect}[1]{\boldsymbol{#1}}
y_i = \beta_1x_{i1}+\beta_2x_{i2}+...+\beta_px_{ip}+\epsilon

y = \vect{X}\beta+\epsilon

\hat{\vect{\beta}}=(\vect{X}^T\vect{X})^{-1}\vect{X}^T\vect{y}
```
see also:
[wiki/Ordinary_least_squares](https://en.wikipedia.org/wiki/Ordinary_least_squares)
### Coefficient of determination - `$r^2$`
```math
r^2 = 1-\dfrac{SS_{res}}{SS_{tot}}= 1-\dfrac{\sum_i(\hat{y}_i-y_i)^2}{\sum_i(\hat{y}_i-\bar{\hat{y}})^2}
```
Measure of how well the model approximate the real data
`$r^2$`
perfect match: `$r^2`$=0``
always return expected y regardless of inputs: `$r^2`$=1``

#### Advantage:  
1. exact solution
2. fast (when dataset is small)
#### Disadvantage:  
1. not scalable. Required lot of memory when dataset is large
## Gradient Descent
[optimizer/Gradient Descent](../basic/optimizer.html#gradient-descent)


## library implementation
scikit-learn model
[sklearn.linear_model.LinearRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)

// TODO: where should it put?
# PCA - Principal components analysis