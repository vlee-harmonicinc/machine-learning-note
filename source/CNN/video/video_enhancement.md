# Video Enhancement
<!--
## DUF
[Deep video super-resolution network using **dynamic upsampling filters** without explicit motion compensation (CVPR 2018)](https://yhjo09.github.io/files/VSR-DUF_CVPR18.pdf)  
[tensorflow](https://github.com/yhjo09/VSR-DUF)
-->

## TOFlow
[Video Enhancement with Task-Oriented Flow (IJCV 2019)](http://toflow.csail.mit.edu/toflow_ijcv.pdf)
**T**ask-**O**riented **Flow** (TOFlow or TOF), a motion representation learned in a selfsupervised, task-specific manner. 

## EDVR
[EDVR: Video Restoration with Enhanced Deformable Convolutional Networks (CVPR 2019)](https://arxiv.org/abs/1905.02716) from SenseTime, CUHK  
[Project](https://xinntao.github.io/projects/EDVR) | [pyTorch (deperciated)](https://github.com/xinntao/EDVR) | [MMSR](https://github.com/open-mmlab/mmsr)
![](https://xinntao.github.io/projects/EDVR_src/arch.png)
##### Pre-deblur
The existence of blur increases the difficulty of motion estimation. EDVR acquire information from multiple frames using alignment, with a slight modification that an image deblurring module is added prior to alignment when there is a blur.
##### PCD
**Pyramid, Cascading and Deformable convolution**: learn good embedding aligned with next frame
##### TSA
Fuse features of 5 or 7 neighbor frames with **Temporal and Spatial Attention**  
**Left**: PCD alignment module with Pyramid, Cascading and Deformable convolution; **Right**: TSA fusion module with Temporal and Spatial Attention
![](https://xinntao.github.io/projects/EDVR_src/pcd_tsa.jpg)

## Zooming Slow-Mo
[Video Frame Interpolation/Zooming Slow-Mo (CVPR 2020)](video_frame_interpolation.html#zooming-slow-mo)
