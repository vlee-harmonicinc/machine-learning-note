# Optimizer
## Gradient Descent/ SGD
// TODO

see also:
[Linear Regression-Gradient Descent](linear_regression.html#stochastic-gradient-descent)
## Momentum
## AdaGrad
adaptive learning rate during training
consider only the sum of the magnitude of previous gradients

## AdaDelta
## RMSprop (Root Mean Square Prop)
consider only the magnitude of gradient of immediate previous iteration
## Adam
Momentum + RMSProp
## EVE
Adam + further adjust learning rate by the ratio of change of input after updating weight

## Cyclical Learning Rates
[Cyclical Learning Rates for Training Neural Networks (WACV 2017)](https://arxiv.org/abs/1506.01186)  
### LR Range test 
### Cyclical Learning Rates
Note: Even though some said the performance of cyclical learning rate is not significant, the concept of LR range test used for other cycle/restart based optimizer

## SGDR
[SGDR: Stochastic Gradient Descent with Warm Restarts (ICLR 2017)](https://arxiv.org/abs/1608.03983)  
SGD with cyclical restart  
avoid local minimium, useful in many model, e.g. EDVR
