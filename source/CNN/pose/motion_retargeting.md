# Motion Retargeting

## PoseWarp
[Synthesizing images of humans in unseen poses (CVPR 2018)](https://openaccess.thecvf.com/content_cvpr_2018/CameraReady/1978.pdf)  
[CVPR 2018 Oral](https://youtu.be/XWr0Fg5XbPs?t=1970) | [Keras](https://github.com/balakg/posewarp-cvpr2018)  
training on pairs of images within the **same** video

## LCM
[Learning Character-Agnostic Motion for Motion Retargeting in 2D (SIGGRAPH 2019)](https://arxiv.org/abs/1905.01680)  
[Project](https://motionretargeting2d.github.io/) | [pyTorch 0.4](https://github.com/ChrisWu1997/2D-Motion-Retargeting)  
Train a deep neural network to decompose temporal sequences of 2D poses into three components: **motion, skeleton, and camera view-angle**. Having extracted such a representation, we are able to re-combine motion with novel skeletons and camera views, and decode a retargeted temporal sequence. 
Pose transfer/ performance cloning is not focus of this paper. It apply [Deep Video-Based Performance Cloning (2018)](https://arxiv.org/pdf/1808.06847.pdf) directly with skeleton retarget instead of global scaling.
![img](https://motionretargeting2d.github.io/images/recompose.gif)  
dataset: synthetic paired data

## EDN
[Everybody dance now (ICCV 2019)](https://arxiv.org/pdf/1808.07371.pdf)  
[Project](https://carolineec.github.io/everybody_dance_now/) | [not available for public] | [reproduce in pyTorch](https://github.com/CUHKSZ-TQL/EverybodyDanceNow_reproduce_pytorch)  
![img](https://carolineec.github.io/everybody_dance_now/images/iccvposter_teaser.jpeg)
### Pose Encoding and Normalization
Encoding body poses + Global pose normalization 
### Pose to Video Translation
Frame-by-frame synthesis + Temporal smoothing + Face GAN
### Dataset
* target(person): five long single-dancer videos that can be used to train and evaluate our (personalized) model
* source(motion): large collection of short YouTube videos that can be used for transfer and fake detection. 

## TransMoMo
[TransMoMo: Invariance-Driven Unsupervised Video Motion Retargeting (CVPR 2020)](https://openaccess.thecvf.com/content_CVPR_2020/papers/Yang_TransMoMo_Invariance-Driven_Unsupervised_Video_Motion_Retargeting_CVPR_2020_paper.pdf)  
[Project](https://yzhq97.github.io/transmomo/) | [pyTorch](https://github.com/yzhq97/transmomo.pytorch)  
![img](https://yzhq97.github.io/assets/transmomo/framework.png)
1. Skeleton Extraction: OpenPose or DensePose
1. **Motion Retargeting Network**
1. Skeleton-to-Video Rendering: [Everybody Dance Now](#edn)
### comparing to LCM
* LCM use synthetic paired data, TransMoMo is pure unlabeled web data
