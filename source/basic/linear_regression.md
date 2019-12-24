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
#### Advantage:  
1. exact solution
2. fast (when dataset is small)
#### Disadvantage:  
1. not scalable. Required lot of memory when dataset is large
## Stochastic Gradient Descent
### 


## library implementation
scikit-learn model
[sklearn.linear_model.LinearRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)

// TODO: where should it put?
# PCA - Principal components analysis