# Human Synthesis
also see [Video Synthesis](../video/video_synthesis.md)
<!--
Pose-to-Body - focuse on pose, single image
video synthesis - focuse on sequences of image
-->

## Types
A. Train a uniform generator for different videos. Reference appearance frame and pose/motion are input as condition during inference.  
B. Train a generator on frames of **same** video. The appearance is encoded in the model. Only pose/motion input is required during inference.  
Generally, type B seems give nicer result with less artifact, but need to re-train a new model for each traget person. Used in motion re-target papers.
type B:  
- vid2vid
- Deep Video-Based Performance Cloning
- Everybody Dance Now

## `$PG^2$`
[Pose Guided Person Image Generation (NIPS 2017)](https://arxiv.org/abs/1705.09368)  
[python 2.7 + tensorflow-gpu 1.4.1](https://github.com/charliememory/Pose-Guided-Person-Image-Generation)  
![](https://raw.githubusercontent.com/charliememory/Pose-Guided-Person-Image-Generation/master/imgs/Paper-framework.svg)

## PoseWarp
[Synthesizing images of humans in unseen poses (CVPR 2018)](https://openaccess.thecvf.com/content_cvpr_2018/CameraReady/1978.pdf)  
[CVPR 2018 Oral](https://youtu.be/XWr0Fg5XbPs?t=1970) | [Keras](https://github.com/balakg/posewarp-cvpr2018)  
Source	Image	Segmentation + Spatial Transformation + Foreground	Synthesis + Background Synthesis

## VUNet
[A Variational U-Net for Conditional Appearance and Shape Generation (CVPR 2018)](https://openaccess.thecvf.com/content_cvpr_2018/papers/Esser_A_Variational_U-Net_CVPR_2018_paper.pdf)  
[Project](https://compvis.github.io/vunet/) | [tensorflow >= 1.3.0](https://github.com/CompVis/vunet)  
![](https://raw.githubusercontent.com/CompVis/vunet/master/assets/cvpr2018_large.gif)
![](https://compvis.github.io/vunet/images/deepfashion_transfer.png)

## Pose Guided Human Video Generation
[Pose Guided Human Video Generation (ECCV 2018)](https://openaccess.thecvf.com/content_ECCV_2018/papers/Ceyuan_Yang_Pose_Guided_Human_ECCV_2018_paper.pdf)

## vid2vid
[vid2vid (NeurIPS 2018)](../video/video_synthesis.md#vid2vid)  
![](https://github.com/NVIDIA/vid2vid/raw/master/imgs/pose.gif)

## Deep Video-Based Performance Cloning
[Deep Video-Based Performance Cloning (Eurographics 2019)](https://arxiv.org/pdf/1808.06847.pdf)

## Progressive Pose Attention Transfer for Person Image Generation
[Progressive Pose Attention Transfer for Person Image Generation (CVPR 2019)](https://openaccess.thecvf.com/content_CVPR_2019/papers/Zhu_Progressive_Pose_Attention_Transfer_for_Person_Image_Generation_CVPR_2019_paper.pdf)  
[PyTorch 0.3.1 or 1.0](https://github.com/tengteng95/Pose-Transfer)
<p float="center">
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/women1.jpg' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/walkfront.gif' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/women2.jpg' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/dance.gif' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/women3.jpg' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/dance2.gif' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/women4.jpg' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/dance3.gif' width="100"/>
</p>

## Everybody Dance Now
[EDN (ICCV 2019)](./motion_retargeting.md#EDN) skeleton-to-rendering part
![](https://carolineec.github.io/everybody_dance_now/images/teaser.png)

<!--
## DwNet
[DwNet: Dense warp-based network for pose-guided human video generation (BMVC 2019)]()  
[Python 2, pyTorch 1.0.1 ](https://github.com/UBC-Computer-Vision-Group/DwNet)
![](https://raw.githubusercontent.com/UBC-Computer-Vision-Group/DwNet/master/demo/teaser.png)
-->

## Liquid Warping GAN
[Liquid Warping GAN: A Unified Framework for Human Motion Imitation,
Appearance Transfer and Novel View Synthesis (ICCV 2019)](https://arxiv.org/pdf/1909.12224.pdf)  
[SVIP Website](https://svip-lab.github.io/project/impersonator.html) | [PyTorch: svip-lab/impersonator](https://github.com/svip-lab/impersonator)  
** type A  
![](https://svip-lab.github.io/project_img/impersonator/pipeline.png)
* 3D body mesh recovery module to *disentangle the pose and shape*, which not only model the joint location and rotation but also characterize the personalized body shape. 
* To *preserve the source information*, such as texture, style, color, and face identity, we propose a **Liquid Warping GAN with Liquid Warping Block (LWB)** that propagates the source information in both image and feature spaces, and synthesizes an image with respect to the reference. Specifically, the source features are extracted by a denoising convolutional auto-encoder for characterizing the source identity well. 
* Furthermore, our proposed method is able to support a more *flexible warping from multiple sources*. 
* In addition, we build a *new dataset*, namely Impersonator (iPER) dataset, for the evaluation of human motion imitation, appearance transfer, and novel view synthesis.

**Body Mesh Recovery Modules**  
HMR - [End-to-end Recovery of Human Shape and Pose (CVPR 2018)](https://arxiv.org/pdf/1712.06584.pdf) as 3D pose and shape estimator due to its good trade-off between accuracy and efficiency  
**Flow composition Module**  
NMR - [Neural 3d mesh renderer](https://arxiv.org/abs/1711.07566) a fully differentiable renderer  
**Liquid Warping GAN**  
1. synthesizes the background image; 
2. predicts the color of invisible parts based on the visible parts; 
3. generates pixels of clothes, hairs and others out of the reconstruction of SMPL

`$G_{BG}$`: output realistic background image `$\hat{I}_{bg}$`  
`$G_{SID}$`: source identity stream, auto-encoder  
`$G_{TSF}$`: transfer stream  
**Liquid Warping Block**: links the source with target streams. It blends the source features from `$G_{SID}$` and fuses them into transfer stream `$G_{TSF}$`. LWB addresses multiple sources, such as in human appearance transfer, preserving the head of source one, and wearing the upper outer garment from the source two, while wearing the lower outer garment from the source
three.


### Impersonator++
[Liquid Warping GAN with Attention: A Unified Framework for Human Image Synthesis (2020)](https://arxiv.org/abs/2011.09055)  
[Website](https://www.impersonator.org/work/impersonator-plus-plus.html) | [iPERDance/iPERCore](https://github.com/iPERDance/iPERCore)  
![](https://www.impersonator.org/images/training.png)