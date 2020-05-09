# Weight Initialization
Aim: keep the variance the same, so there is gradient for back propagration
## Unsupervised pre-training
e.g. VAE
## Xavier Initialization
Also known as Glorot initialization.  
[Understanding the difficulty of training deep feedforward neural networks (AISTATS 2010)](http://proceedings.mlr.press/v9/glorot10a/glorot10a.pdf): 4.2 Gradients at initialization  
based on logistic sigmoid activation function  
## Kaiming Initialization
Also known as He initialization  
[Delving deep into rectifiers: Surpassing human-level performance on ImageNet classification (ICCV 2015)](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/He_Delving_Deep_into_ICCV_2015_paper.pdf): 2.2. Initialization of Filter Weights for Rectifiers  
Designed for ReLU