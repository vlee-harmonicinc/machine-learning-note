# Tracking
1. with sequence of detection results, matchs same object
2. with reference frame, keep tracking same object

# Tracking Based on detection sequence
Multi-Object Tracking Challenge:[MOT Challenge](https://motchallenge.net/)  
Great summay: [Multi-Object-Tracking-Paper-List](https://github.com/SpyderXu/multi-object-tracking-paper-list)
## SORT (ICIP 2016)
[Simple Online and Realtime Tracking](https://arxiv.org/abs/1602.00763)  
signal filter: Kalman Filter + Hungarian algorithm  
tempo smoothing  
[Notes for Kalman filtering](https://www.bzarg.com/p/how-a-kalman-filter-works-in-pictures/)
Official code: [Python 2.7](https://github.com/abewley/sort)
## deepSORT (ICIP 2017)
[Simple Online and Realtime Tracking with a Deep Association Metric](https://arxiv.org/abs/1703.07402)  
SORT: singal filtering (Kalman filtering + Hungarian algorithm)
deep: neural network model for embedding feature of the image within bounding boxes

# Single Object Tracking Based on reference frame
OTB Challenge and VOT Challenge  
## Filtering
### KCF
### CCOT
### ECO (CVPR 2017)
[ECO: Efficient Convolution Operators for Tracking](https://arxiv.org/abs/1611.09224)

## SiamFC
### v1 (ECCV 2016), v2 (CVPR 2017)
[Fully-Convolutional Siamese Networks for Object Tracking](http://www.robots.ox.ac.uk/~luca/siamese-fc.html)  
Siamese Network: [Siamese network](/basic/basic_models.html#siamese-network-1993)  

## SiameseRPN (CVPR 2018)
[High Performance Visual Tracking with Siamese Region Proposal Network](http://openaccess.thecvf.com/content_cvpr_2018/papers/Li_High_Performance_Visual_CVPR_2018_paper.pdf)  
adding [Proposal Regression Network](/CNN/object_detection/object_detection.html#region-proposal-network-rpn)  
## DaSiamRPN (ECCV 2018)
[Distractor-aware Siamese Networks for Visual Object Tracking](https://arxiv.org/abs/1808.06048)  
Da: Distractor-aware  
[ECCV视觉目标跟踪之DaSiamRPN](https://zhuanlan.zhihu.com/p/42546692)  
> 在做完SiamRPN之后，我们发现虽然跟踪的框已经回归地比较好了，但是响应的分数仍然相当不可靠，具体表现为在丢失目标的时候，分类的分数仍然比较高（例如0.8+），换句话说，其实我们推断SiamRPN只是学习到了objectness/non-objectness的区分
* 加入detection的图片数据, pair可以由静态图片通过数据增益生成；加入detection数据生成的正样本之后，模型的泛化性能得到了比较大的提升. 
* 用不同类之间的样本（还有同类的不同instance）构建难例负样本，从而增强分类器的判别能力
## SiamMask
## SiamRPN++ (CVPR 2019)
[SiamRPN++: Evolution of Siamese Visual Tracking with Very Deep Networks](http://openaccess.thecvf.com/content_CVPR_2019/papers/Li_SiamRPN_Evolution_of_Siamese_Visual_Tracking_With_Very_Deep_Networks_CVPR_2019_paper.pdf)
[视觉目标跟踪之SiamRPN++](https://zhuanlan.zhihu.com/p/56254712)

## Extra
[[CVPR2019\]我对Siamese网络的一点思考（SiamMask）](https://zhuanlan.zhihu.com/p/58154634)

