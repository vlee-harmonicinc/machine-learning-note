# Normalization
## Batch Normalization (2015)
[Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift](https://arxiv.org/abs/1502.03167)
normalize x based on value over all values within same mini-batch
used before activiation function
usage:
1. reduce [Internal Covariate Shift](/issue#Internal Covariate Shift)
1. avoid [Gradient Vanishing](/issue#Gradient Vanishing)
1. as regularizer to minize need of dropout (reduce overfiting)
![](img/batchNorm_ICS.png)

For Prediction, use population mean and population variance calucated during training.  
the effectiveness diminishes when the training minibatches are small.  
alt: Batch Renormalization  
not suggested to use with WGAN-GP  

wdsr use weightnorm instead of batchnorm because:  
for image super-resolution, only small patches nsed, thus the mean and variance differ  
BN act as regularizer. super-resolution rarly overfit training dataset  
Unlike image classification tasks where softmax (scale-invariant) is used at the end of networks to make prediction, for super-resolution , the different formulation of training and testing may deteriorate the accuracy for dense pixel value prediction.

## Layer Normalization
no batch size required.  
for shared weight model, e.g. RNN, CNN(but not good for CNN)  
might reduce the representivity of model  

## Weight Normalization (NIPS 2016)
[Weight Normalization: A Simple Reparameterization to Accelerate Training of Deep Neural Networks](https://arxiv.org/abs/1602.07868)
reduce computation cost  
unstable on training, high dependency of input data  

## Cosine Normalization (2017)
[Cosine Normalization: Using Cosine Similarity Instead of Dot Product in Neural Networks](https://arxiv.org/abs/1702.05870)

## SELU
[Activation functions/SELU](activation_functions.html#selu-scaled-exponential-linear-unit-nips-2017)