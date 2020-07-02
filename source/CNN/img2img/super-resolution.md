# Super-resolution


some cross-project repo:
[Martin Krasser/Keras-super-resolution](https://github.com/krasserm/super-resolution): SRGAN, EDSR, WDSR  
[open-mmlab/MMSR](https://github.com/open-mmlab/mmsr): SRResNet, SRGAN, ESRGAN, EDVR, etc.
## SRCNN
[Image Super-Resolution Using Deep Convolutional Networks (TPAMI 2014)](https://arxiv.org/abs/1501.00092) by CUHK  
[Project](http://mmlab.ie.cuhk.edu.hk/projects/SRCNN.html) - include Matlab and Caffe code  
first upscale it to the desired size using bicubic interpolation
### FSRCNN
[Accelerating the Super-Resolution Convolutional Neural Network (ECCV 2016)](https://arxiv.org/abs/1608.00367) by CUHK  
use deconvolution to upscale instead of pre-processing  
## VDSR
[Accurate Image Super-Resolution Using Very Deep Convolutional Networks (CVPR 2016)](https://arxiv.org/abs/1511.04587)  
start to use residual, one long skip-connection  
![](img/VDSR.png)  
Same as SRCNN, it take upscaled LR image as imput  

## SRGAN
[Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network (CVPR 2017)](https://arxiv.org/abs/1609.04802) by Twitter  
[Tensorflow 2.0](https://github.com/tensorlayer/srgan)  
SRResNet + long skip-connection, diverge from MSE
**novel** perceptual loss using high-level feature maps of VGG network  

## EDSR
[Enhanced Deep Residual Networks for Single Image Super-Resolution (CVPR 2017)](https://arxiv.org/abs/1707.02921)
remove batch normalization of [SRResNet](#srgan-cvpr-2017)→ save resource 
spend resource on convolution instead
### MDSR
multiscale architecture that reconstructs various scales of high-resolution images in a single model

## WDSR
[Wide Activation for Efficient and Accurate Image Super-Resolution (CVPR Workshop 2018)](https://arxiv.org/abs/1808.08718)  
[Official pyTorch (based on EDSR)](https://github.com/JiahuiYu/wdsr_ntire2018) | [tensorflow](https://github.com/ychfan/tf_estimator_barebone/) 
![](img/WDSR_block.png)  
* increase channel before ReLU 
* linear low-rank convolution stack and large channel

## SFTGAN
[Recovering Realistic Texture in Image Super-resolution by Deep Spatial Feature Transform (CVPR 2018)](https://openaccess.thecvf.com/content_cvpr_2018/papers/Wang_Recovering_Realistic_Texture_CVPR_2018_paper.pdf) - SenseTime  
**Spatial Feature Transform**: learns a mapping function `$M$` that outputs a modulation parameter pair (γ, β)
generate affine transformation parameters for spatial-wise feature modulation  
![](img/SFTGAN_architecture.png)
* Could add categorical prior
![](img/SFTGAN.png)

## RDN
[Residual Dense Network for Image Super-Resolution (CVPR 2018)](https://openaccess.thecvf.com/content_cvpr_2018/papers/Zhang_Residual_Dense_Network_CVPR_2018_paper.pdf)
* Residual + Dense block
* local feature fusion + global feature fusion -> contiguous memory mechanism
used in [video debluring/BIN](../video/video_frame_interpolation.html#bin)

## ESRGAN
[ESRGAN: Enhanced Super-Resolution Generative Adversarial Networks (ECCV 2018)](https://openaccess.thecvf.com/content_ECCVW_2018/papers/11133/Wang_ESRGAN_Enhanced_Super-Resolution_Generative_Adversarial_Networks_ECCVW_2018_paper.pdf) - CUHK  
* RRDB (Residual in Residual Dense Blcok)
* enhance adversarial loss and perceptual loss
* relativistic GAN
* improve the perceptual loss by using the features before activation

