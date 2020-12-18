# Pose

## Hourglass
[Stacked Hourglass Networks for Human Pose Estimation (ECCV 2016)](https://arxiv.org/abs/1603.06937)  
residual module + pooling + upsampling (via interpolation)

## OpenPose
[Realtime Multi-Person 2D Pose Estimation using Part Affinity Fields (CVPR 2017)](http://openaccess.thecvf.com/content_cvpr_2017/papers/Cao_Realtime_Multi-Person_2D_CVPR_2017_paper.pdf)  
[CMU-Perceptual-Computing-Lab/openpose](https://github.com/CMU-Perceptual-Computing-Lab/openpose) -  commercial license required
### HyperPose
re-implemented of OpenPose by tensorlayer. Version 2 of OpenPose Plus  
[tensorlayer/hyperpose](https://github.com/tensorlayer/hyperpose): A Fast & Flexible Library for Human Pose Estimation - Apache 2.0 license

## CPN
[Cascaded pyramid network for multi-person pose estimation (CVPR 2018)](https://arxiv.org/abs/1711.07319)  
[tensorflow](https://github.com/chenyilun95/tf-cpn)

## HMR
[End-to-end Recovery of Human Shape and Pose (CVPR 2018)](https://arxiv.org/pdf/1712.06584.pdf)  
**H**uman **M**esh **R**ecovery
Generate 3D Mesh from 2D image  
used by Liquid Warpping GAN  

## MSPN
[Rethinking on Multi-Stage Networks for Human Pose Estimation (2019)](https://arxiv.org/abs/1901.00148)  
> Existing pose estimation approaches fall into two categories: single-stage and multi-stage methods. While multistage methods are seemingly more suited for the task, their performance in current practice is not as good as singlestage methods. This work studies this issue. We argue that the current multi-stage methods’ unsatisfactory performance comes from the insufficiency in various design choices. We propose several improvements, including the single-stage module design, cross stage feature aggregation, and coarse-tofine supervision.  

[pytorch](https://github.com/fenglinglwb/MSPN)

## Soft-gated Skip Connections
[Toward fast and accurate human pose estimation via soft-gated skip connections (FG 2020)](https://arxiv.org/pdf/2002.11098.pdf)
