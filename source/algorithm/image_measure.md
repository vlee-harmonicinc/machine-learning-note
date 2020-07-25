# Image Measure
## MSE
## PSNR
## SSIM
```math
\text{SSIM}(x,y) = \left[ l(x,y)^\alpha \cdot c(x,y)^\beta \cdot s(x,y)^\gamma \right]                
```
l: luminance, c: contrast, s: structure  
```math
l(x,y)=\frac{2\mu_x\mu_y + c_1}{\mu^2_x + \mu^2_y + c_1} \\
c(x,y)=\frac{2\sigma_x\sigma_y + c_2}{\sigma_x^2 + \sigma_y^2 + c_2} \\
s(x,y)=\frac{\sigma_{xy} + c_3}{\sigma_x \sigma_y + c_3}
```
c: constant depend on dynamic range of pixel value  

```math
\text{SSIM}(x,y) = \frac{(2\mu_x\mu_y + c_1)(2\sigma_{xy} + c_2)}{(\mu_x^2 + \mu_y^2 + c_1)(\sigma_x^2 + \sigma_y^2 + c_2)}
```

## MOS
MOS stands for **M**ean **O**pinion **S**core, rated by human
## LPIPS
LPIPS stands for **L**earned **P**erceptual **I**mage **P**atch **S**imilarity
[The Unreasonable Effectiveness of Deep Features as a Perceptual Metric(CVPR 2018)](https://openaccess.thecvf.com/content_cvpr_2018/papers/Zhang_The_Unreasonable_Effectiveness_CVPR_2018_paper.pdf)  
[Project](https://richzhang.github.io/PerceptualSimilarity/) | [pyTorch 1.0+](https://github.com/richzhang/PerceptualSimilarity)
Higher means further/more different. Lower means more similar.
### GAN
LPIPS could also used to measure the average feature distances between generated samples. 
Higher LPIPS scores indicate better diversity among the generated images.
