# Video Deblurring
cross-reference: [Image Deblurring](../img2img/deblurring.md)

## DVD
[Deep Video Deblurring for Hand-held Cameras (CVPR 2017)](https://openaccess.thecvf.com/content_cvpr_2017/papers/Su_Deep_Video_Deblurring_CVPR_2017_paper.pdf)
[Project](http://www.cs.ubc.ca/labs/imager/tr/2017/DeepVideoDeblurring/) | [Matlab, Lua](https://github.com/shuochsu/DeepVideoDeblurring)

## EDVR
[Video Enhancement/EDVR](video_enhancement.html#edvr)

## IFI-RNN
[Recurrent Neural Networks with Intra-Frame Iterations for Video Deblurring (CVPR 2019)](https://openaccess.thecvf.com/content_CVPR_2019/papers/Nah_Recurrent_Neural_Networks_With_Intra-Frame_Iterations_for_Video_Deblurring_CVPR_2019_paper.pdf)  
No source code?

## STFAN
[Spatio-Temporal Filter Adaptive Network for Video Deblurring (ICCV 2019)](https://openaccess.thecvf.com/content_ICCV_2019/papers/Zhou_Spatio-Temporal_Filter_Adaptive_Network_for_Video_Deblurring_ICCV_2019_paper.pdf) - SenseTime + Nanjing University of Science and Technology  
[Project](https://shangchenzhou.com/projects/stfan/) | [PyTorch 1.0](https://github.com/sczhou/STFAN)
> 1. We propose a filter adaptive convolutional (FAC) layer that **applies the generated element-wise filters** to feature transformation, which is utilized for two spatially variant tasks, i.e. alignment and deblurring in the feature domain.
> 1. We propose a novel spatio-temporal filter adaptive network (STFAN) for video deblurring. It integrates the frame alignment and deblurring into a unified framework without explicit motion estimation and formulates them as two spatially variant convolution process based on the FAC layers.
![small_img](https://shangchenzhou.com/projects/assets/img/stfan/fac.jpg)

## CDVD-TSP
[Cascaded Deep Video Deblurring Using Temporal Sharpness Prior (CVPR 2020)](https://openaccess.thecvf.com/content_CVPR_2020/papers/Pan_Cascaded_Deep_Video_Deblurring_Using_Temporal_Sharpness_Prior_CVPR_2020_paper.pdf) - Nanjing University of Science and Technology  
[Project](https://baihaoran.xyz/projects/cdvd-tsp/index.html) |
[PyTorch code](https://github.com/csbhr/CDVD-TSP)
> * We propose a simple and compact deep CNN model that simultaneously **estimates the optical flow**(PWC-Net) and latent frames for video deblurring.
> * To better explore the properties of consecutive frames, we develop a **temporal sharpness prior** to constrain deep CNN models. 
###### Other Note: Motion blur
TSP is designed for hand-held cameras dataset from [DVD](#dvd) based on below assumption
> As demonstrated in [4], the blur in the video is irregular, and thus there exist some pixels that are not blurred. Following the conventional method [4], we explore these sharpness pixels to help video deblurring.  

Hence it might not suitable for continuous motion blur (e.g. racing)

## BIN
[Frame interpolation/BIN](video_frame_interpolation.html#bin)
