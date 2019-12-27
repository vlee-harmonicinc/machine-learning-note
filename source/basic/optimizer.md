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



P.S. WGAN paper: Momentum based optimizer do not suit GAN