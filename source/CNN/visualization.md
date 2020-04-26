# Visualization
Model explaination for CNN
## GAP
[CNN/Network In Network(ICLR 2014)](models.html#nin-iclr-2014)
**global average pooling layer** (GAP) pool average value of whole feature map + softmax activation, replace fully connected layer in last layer of classification model. 
1. GAP enforce the correspondence between feature maps and categories for visualization.
1. prevent overfit and make CNN interpretable. 
1. fully convolutional

## CAM (CVPR 2016) 
[Learning Deep Features for Discriminative Localization](http://cnnlocalization.csail.mit.edu/Zhou_Learning_Deep_Features_CVPR_2016_paper.pdf)
### Class Activation Map
revisit **global average pooling layer** via connect to fully connected layer  
multiply last CNN layer before [GAP](#gap) with weight of fully connected layer  
1. weakly supervised. Transfer the activation map learnt from classification (with simple object label) to other task like object segmentation, image regression)
1. visualizatoin with weighting of fully connnected layer.

## Grad-CAM (ICCV 2017)
[Grad-CAM: Visual Explanations from Deep Networks via Gradient-based Localization](http://openaccess.thecvf.com/content_ICCV_2017/papers/Selvaraju_Grad-CAM_Visual_Explanations_ICCV_2017_paper.pdf)  
Using gradiant of backpropagation to find the weight of CAM **without GAP**. Hence Grad-CAM could be applied to many well-designed models.
```math
\alpha^c_k = 
\overbrace{
\frac{1}{Z}
\sum_i
\sum_j
}^{\text{global average pooling}}
\underbrace{\frac{\partial y^c}{\partial A^k_{ij}}}_{\text{gradients via backprop}} 
```

### Guided Grad-CAM
element-wise multiple **guided backpropagation** from [Striving for Simplicity: The All Convolutional Net (ICLR 2015)](https://arxiv.org/pdf/1412.6806.pdf) to edge, stripe, texture etc