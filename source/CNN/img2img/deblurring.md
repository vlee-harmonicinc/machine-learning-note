# deblurring
## Type of blur or noise
* Motion Blur
* Out of Focus
* Low-resolution
* Encoding Noise
The first one related to video
## Learning a convolutional neural network for non-uniform motion blur removal (CVPR 2015)
## Blind Image Deconvolution by Automatic Gradient Activation (CVPR 2016)
## DeepDeblur (CVPR 2017)
[github](https://github.com/SeungjunNah/DeepDeblur_release)
* new dataset: [REDS](https://seungjunnah.github.io/Datasets/reds) 
## Self-paced Kernel Estimation for Robust Blind Image Deblurring (ICCV 2017)
## blur2mflow (CVPR 2017)
[From Motion Blur to Motion Flow: a Deep Learning Solution for Removing Heterogeneous Motion Blur](https://donggong1.github.io/docs/blur2mflow_cvpr17.pdf)
[Project](https://donggong1.github.io/blur2mflow)
estimate motion flow and use then estimated motion flow to recover the unblurred image
![](https://donggong1.github.io/projects/blur2mflow/framework.jpg)
![](https://donggong1.github.io/projects/blur2mflow/net.png)
## DeblurGAN (CVPR 2018)
[DeblurGAN: Blind Motion Deblurring Using Conditional Adversarial Networks](https://arxiv.org/pdf/1711.07064.pdf)  
[pyTorch](https://github.com/KupynOrest/DeblurGAN)| [Keras re-implementation](https://github.com/RaphaelMeudec/deblur-gan)  
0.3fps for 1280x720 on GTX1080 Ti (`python3 test.py --dataroot <folder> --model test --dataset_mode single --learn_residual --loadSizeX 1280 --loadSizeY 720 --resize_or_crop ''`)
Requirement of running pre-trained weights:
```
pyTorch version 0.3.1 with cuda 9.0 (because 9.2 and 10.0 have not pyTorch wheel provided)
torchvision 0.2.0
torchtext 0.2.3
revert NINJA commit (b15a520d660e4366e10bd1110398c731da1f1f6c)
```
### DeblurGAN-v2 (ICCV 2019)
[DeblurGAN-v2: Deblurring (Orders-of-Magnitude) Faster and Better](https://arxiv.org/abs/1908.03826)
[pyTorch](https://github.com/TAMU-VITA/DeblurGANv2)