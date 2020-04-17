# GAN Metrics
## Inception Score
using Inception V3 get 1000 output class vector  
based on assumption
1. a real photo have higher probably belong to 1 class
2. a good generative model should output different class
## Fréchet Inception Distance (FID)
use feature instead of final output
## Precision, Recall and F1 Score

## Learned Perceptual Image Patch Similarity (LPIPS)
[The Unreasonable Effectiveness of Deep Features as a Perceptual Metric(CVPR 2018)](https://zpascal.net/cvpr2018/Zhang_The_Unreasonable_Effectiveness_CVPR_2018_paper.pdf)
to measure the average feature distances between generated samples. Higher LPIPS scores indicate better diversity among the generated images.
