# Matting
## Deep Automatic Portrait Matting
[Deep Automatic Portrait Matting (ECCV 2016)](http://www.cse.cuhk.edu.hk/~leojia/projects/automatting/papers/deepmatting.pdf)  
[Project](http://www.cse.cuhk.edu.hk/~leojia/projects/automatting/)  
![img](http://www.cse.cuhk.edu.hk/~leojia/projects/automatting/figures/teaser.png)
> First, pixels are classified into background, foreground and unknown labels based on fully convolutional networks with several new components. For the second part, we propose the novel matting layer with forward and backward image matting formation. These two functions are incorporated in the unified end-to-end system without user interaction.

CNN + novel matting layer (closed-form or KNN, manually pick better matting for training dataset)
### data
For training, the model requires portrait image `$I$`, trimap label `$F^s, B^s, U^s$` and a face feature template`$P_{template}$`. During training, it generates face feature points `$P$` and compute homography transformation `$T$` with `$P$` and `$P_{template}$`, for compute algined *shape mask* `$M$`, indicate as (a) in fig 3 used for backprop.
```math
P_{template}=T_i(P_i)\\
M_{GT}=T_i(M_i)
```
Then backpropagate shape mask `$M_{GT}$` with 4th channel of stage one CNN output `$M$`. Training with shape mask reduce matting for pixels far from the portrait region.  
For inference, only the portrait image `$I$` is required.  
## DIM
[Deep Image Matting (CVPR 2017)](https://arxiv.org/pdf/1703.03872.pdf) - Adobe  
[Project](https://sites.google.com/view/deepimagematting)  
Adobe Deep Image Matting Dataset: not public :(

## LFM
[A Late Fusion CNN for Digital Matting (CVPR 2019)](http://openaccess.thecvf.com/content_CVPR_2019/papers/Zhang_A_Late_Fusion_CNN_for_Digital_Matting_CVPR_2019_paper.pdf)  
[Project page on github, with Keras code in OneDrive](https://github.com/yunkezhang/FusionMatting)
### Question
[[质疑\][CVPR2019\][A Late Fusion CNN for Digital Matting\]](https://zhuanlan.zhihu.com/p/127195671), 
[Author's reply](https://zhuanlan.zhihu.com/p/128146732)
> 我们放出的model是在DIM上pretrain，然后在Human Matting Dataset上finetune的model. 
> due to Alibaba's policy we cannot share our human matting dataset currently

## Background Matting: The World is Your Green Screen
[Background Matting: The World is Your Green Screen (CVPR 2020)](https://arxiv.org/abs/2004.00626)  
[Project](http://grail.cs.washington.edu/projects/background-matting/) | [pyTorch](https://github.com/senguptaumd/Background-Matting)