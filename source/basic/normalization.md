# Normalization
PS: usually use before activication
## Local Response Normalization
LRN from [AlexNet](/CNN/models.html#alexnet)  
```math
b^i_{x,y}=\frac{a^i_{x,y}}{\Big(k+\frac{\alpha}{n}\sum^{min(N-1, c+n/2)}_{c=max(0,i-n/2)} (a^c_{x,y})^2 \Big)^\beta}
```
sum runs over n “adjacent” kernel maps at the same spatial position, and N is the total number of kernels in the layer. The ordering of the kernel maps is of course arbitrary and determined before training begins. This sort of response normalization implements a form of **lateral inhibition** inspired by the type found in real neurons, creating competition for big activities amongst neuron outputs computed using different kernels.  
In later development, it is claimed that LRN is not useful.

### Pixelwise Feature Vector Normalization (ICLR 2018)
from [Progressive GAN](/GAN/GAN_image2image.html#progressive-gan-iclr-2018)
variant of LRN with all channels, i.e. n=N
```math
b_{x,y}=\frac{a_{x,y}}{sqrt{\frac1{N}\sum^{N-1}_{j=0}(a^j_{x,y})^2+\epsilon}}
```

## Batch Normalization
[Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift (ICML 2015)](https://arxiv.org/abs/1502.03167)  
normalize x based on value over all values within same mini-batch with mean and variance  
learnable parameters: scale and bias ``$`\gamma, \beta`$``  
For Prediction, use population mean and population variance calucated during training.  
The effectiveness diminishes when the training minibatches are small.  
### Why BatchNorm works?
Origin paper said BatchNorm reduce *Internal Covariate Shift*: the change in the distribution of network activations due to the change in network parameters during training.  
[How Does Batch Normalization Help Optimization? (NIPS 2018)](https://arxiv.org/abs/1805.11604) demonstrate is NOT Internal covariate shift and suggest it makes the optimization **landscape** significantly **smoother**. 

## Layer Normalization (NIPS 2016)
[Layer Normalization](https://arxiv.org/abs/1607.06450)  
no batch size required  
for shared weight model, e.g. RNN, CNN(but not good for CNN)  
might reduce the representivity of model  

## Weight Normalization (NIPS 2016)
[Weight Normalization: A Simple Reparameterization to Accelerate Training of Deep Neural Networks](https://arxiv.org/abs/1602.07868)  
adv: 
1. not relay on batch
1. less noise
1. less computation since not saving avg and variance of batch data  

disadv:
1. need good initialization, high dependency of input data  
1. unstable on training  

## Instance normalization (2016)
[Instance Normalization: The Missing Ingredient for Fast Stylization](https://arxiv.org/abs/1607.08022)  
like batch norm with 1 batch size (still normalize though heightxwidth)  

## SELU (NIPS 2017)
[Activation functions/SELU](activation_functions.html#selu-scaled-exponential-linear-unit-nips-2017)

## Group Normalization (ECCV 2018)
[Group Normalization](https://eccv2018.org/openaccess/content_ECCV_2018/papers/Yuxin_Wu_Group_Normalization_ECCV_2018_paper.pdf)  
![](img/group_norm_comparison.png)

## Conditional BatchNorm (NIPS 2017)
[Modulating early visual processing by language](https://papers.nips.cc/paper/7237-modulating-early-visual-processing-by-language.pdf)  
[pytorch](https://github.com/ap229997/Conditional-Batch-Norm) | [guessWhat?!](https://www.guesswhat.ai)  
``$`\gamma, \beta`$`` learnt from one-hidden-layer MLP rely on input  
used in [cGAN with projection discriminator](/GAN/GAN_representation_learning.html#projection-discriminator) and [SAGAN](/GAN/GAN_general.html#sagan-pmlr-2019)  

## Conditional Instance Normalizatoin (ICLR 2017)
[A learned representation for artistic style](https://arxiv.org/pdf/1610.07629.pdf)

## Adaptive Instance Normalization (ICCV 2017)
also called AdaIN  
[Arbitrary style transfer in real-time with **ada**ptive **i**nstance **n**ormalization](http://openaccess.thecvf.com/content_ICCV_2017/papers/Huang_Arbitrary_Style_Transfer_ICCV_2017_paper.pdf)  
scale with output domain distribution
```math
AdaIN(x,y)=\sigma_y\big(\frac{x-\mu_x }{\sigma_x}\big)+\mu_y
```

## Batch Renormalization (NIPS 2017)
[Batch Renormalization: Towards Reducing Minibatch Dependence in Batch-Normalized Models](https://arxiv.org/pdf/1702.03275.pdf) by Google  
data in batch cannot cover the real data distribution -> batchNorm perform badly
using moving avg mean and SD -> the gradient optimization and the normalization to counteract each other -> model blow up
novel re-normalization apply on x (before scaling)
mean and SD of batch: ``$`\mu_B \sigma_B  `$``  
moving avg (larger than 1 batch) of mean and SD: ``$`\mu \sigma  `$``  
```math
\mu_B    & \leftarrow \frac1{m}\sum^m_{i=1}x_i \\
\sigma_B & \leftarrow \sqrt{\epsilon + \frac1{m}\sum^m_{i=1}(x_i-\mu_B)^2}\\
r        & \leftarrow stop_gradient(clip_{[1/r_{max}, r_{max}]}(\frac{\sigma_B}{\sigma})) \\
d        & \leftarrow stop_gradient(clip_{[-d_{max},d_{max}]})(\frac{\mu_B-\mu}{\sigma})  \\
\hat{x}_i& \leftarrow \frac{x_i-\mu_B}{\sigma_B}\dot r + d
y_i      & \leftarrow \gamma \hat{x}_i + \beta
```
* have higher improvement when the batch small and data distribution diverse, not easy to over-fit
[如何评价batch renormalization？ - 汪汪的回答 - 知乎](https://www.zhihu.com/question/55890057/answer/267872896)

## SPADE
stands for **SP**atially-**A**daptive (**DE**)normalization  
[Semantic Image Synthesis with Spatially-Adaptive Normalization (CVPR 2019)](https://arxiv.org/abs/1903.07291) by Nvidia  
![](https://nvlabs.github.io/SPADE/images/teaser_high_res_uncompressed.png)
solving issue: semantic information washed away through stacks of convolution, normalization, and nonlinearity layers
similar to batchNorm, activation is normalized in the channelwise manner, and then modulated with learned ``$`\gamma, \beta`$``  
Unlike prior conditional normalization, ``$`\gamma, \beta`$`` are not vectors, but tensors with spatial dimensions
![](https://nvlabs.github.io/SPADE/images/method.png)  
using the input layout for modulating the activations in normalization layers through a spatially-adaptive, learned transformation (two-layers convolutional network). 

## Summary and use cases

|  |usable situation|unsuitable application | example model(s)|
|---|---|---|---|
LRN         |                                             AlexNet, ProgressiveGAN(variant n=N with all channels)
BatchNorm   |batch reflect real data distribution|RNN,small batch size,patch based,WGAN-GP|UNet
LayerNorm   |no batch sized required, RNN
WeightNorm  |no batch sized required | |WDSR|
InstanceNorm|instance specified, e.g. img2img|classification|DeblurGAN
SELU        |feed-forward network (FNNs)|CNN, RNN|audio, features based model
GroupNorm   |
BatchReNorm |any BatchNorm with small batch size||[OCR](https://arxiv.org/pdf/1812.11894.pdf)
Conditional BatchNorm|conditional GAN|unconditional|SAGAN
AdaIN       |Style Transfer ||StyleGAN
SPADE       |conditional CNN GAN|unconditional|GauGAN
