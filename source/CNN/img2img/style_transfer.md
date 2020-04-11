# Style Transfer
## Style Transfer using CNN (CVPR 2016)
[A Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576)
[Image Style Transfer Using Convolutional Neural Networks](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf) by Gatys  
unsupervised
input: content image, target style image
loss: content loss + style loss
Could trade-off between content and style  
##### Discussion
The final model is style and image specified, i.e. each image output requires training an individual model. The speed of synthesis procedure depends heavily on image resolution. 512x512 pixels images take an hour on Nvidia K40 GPU.
## Perceptual Loss (ECCV 2016)
[Perceptual Losses for Real-Time Style Transfer and Super-Resolution](https://arxiv.org/pdf/1603.08155.pdf)
Answer above question of Style Transfer using CNN: Style-specified model
**perceptual loss**- compare two image based on high-level representations from pretrained CNN e.g. VGG loss ( pretrained for classification)  

**Feature Reconstruction Loss**: Euclidean distance between feature representation, computed by the loss network  
**Style Reconstruction Loss**: penalize difference in style with perceptual loss  
![](img/perceptual_loss.png)
Content Target y_c = Input Image x

**Total Variation Regularization**: encourage spatial smoothness  
**Kernel loss**  

## More paper
There are a lot [GAN](/latest/generative_models/GAN/index.html) that could handle Style Transfer
