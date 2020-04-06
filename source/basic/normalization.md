# Normalization
## Local Response Normalization (NIPS 2012)
[AlexNet/Local Response Normalization](/CNN/models.html#local-response-normalization)

## Batch Normalization (ICML 2015)
[Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift](https://arxiv.org/abs/1502.03167)
normalize x based on value over all values within same mini-batch with mean and variance  
learnable parameters: scale and bias ``$`\gamma, \beta`$``  
instance normalization ()
seems good for generative task
usage:
1. reduce [Internal Covariate Shift](/issue.html#Internal Covariate Shift)
1. avoid [Gradient Vanishing](/issue.html#Gradient Vanishing)
1. as regularizer to minize need of dropout (reduce overfiting)
![](img/batchNorm_ICS.png)  
usually used before activiation function

For Prediction, use population mean and population variance calucated during training.  
the effectiveness diminishes when the training minibatches are small.  
alt: Batch Renormalization  
not suggested to use with WGAN-GP  

wdsr use weightnorm instead of batchnorm because:  
for image super-resolution, only small patches nsed, thus the mean and variance differ  
BN act as regularizer. super-resolution rarly overfit training dataset  
Unlike image classification tasks where softmax (scale-invariant) is used at the end of networks to make prediction, for super-resolution , the different formulation of training and testing may deteriorate the accuracy for dense pixel value prediction.

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
1. need good initialization
1. unstable on training, high dependency of input data  

## Instance normalization (2016)
[Instance Normalization: The Missing Ingredient for Fast Stylization](https://arxiv.org/abs/1607.08022)  
like batch norm with 1 batch size (still normalize though heightxwidth)  
P.S. used by DeblurGAN  

## Cosine Normalization (2017)
[Cosine Normalization: Using Cosine Similarity Instead of Dot Product in Neural Networks](https://arxiv.org/abs/1702.05870)

## SELU (NIPS 2017)
[Activation functions/SELU](activation_functions.html#selu-scaled-exponential-linear-unit-nips-2017)

## Group Normalization (ECCV 2018)
[Group Normalization](https://eccv2018.org/openaccess/content_ECCV_2018/papers/Yuxin_Wu_Group_Normalization_ECCV_2018_paper.pdf)  
dimension similar to LRN, but using more general normalization formula?
![](img/group_norm_comparison.png)

## Conditional BatchNorm (NIPS 2017)
[Modulating early visual processing by language](https://papers.nips.cc/paper/7237-modulating-early-visual-processing-by-language.pdf)  
[pytorch](https://github.com/ap229997/Conditional-Batch-Norm) | [guessWhat?!](https://www.guesswhat.ai)  
``$`\gamma, \Beta`$`` learnt from one-hidden-layer MLP rely on input  
used in [cGAN with projection discriminator](/generative_models/GAN/GAN_general.html#projection-discriminator-iclr-2018) and [SAGAN](/generative_models/GAN/GAN_general.html#sa-gan-pmlr-2019)  

## Conditional Instance Normalizatoin (ICLR 2017)
[A learned representation for artistic style](https://arxiv.org/pdf/1610.07629.pdf)

## Adaptive Instance Normalization (ICCV 2017)
also called Adain  
[Arbitrary style transfer in real-time with adaptive instance normalization](http://openaccess.thecvf.com/content_ICCV_2017/papers/Huang_Arbitrary_Style_Transfer_ICCV_2017_paper.pdf)  
```math
AdaIN(x,y)=\sigma_y\big(\frac{x-\mu_x }{\sigma_x}\big)+\mu_y
```

## SPADE (CVPR 2019)
[GauGAN/SPADE](/generative_models/GAN/GAN_image2image.html#spade-cvpr-2019)
