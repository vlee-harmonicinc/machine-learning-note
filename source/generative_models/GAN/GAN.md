# GAN
* [General Enhancement](/generative_models/GAN_general.md)
* [Repersentation Learning with GAN](/generative_models/GAN_repersentation_learning.md)
* [image-to-image GAN](/generative_models/GAN_image2image.md)
* [GAN for data augmentation](/generative_models/GAN_for_data_augmentation.md)
* [Adversarial Attacks](/generative_models/adversarial_attacks.md)

## Challenges
### Mode Collapse / Mode Diversity
generator collapses, produces limited varieties of sample to fake discrimator
cuased by: dimension deficient
solutions:  generalized dataset, Orthonormal constraint (正交約束), diversity loss (e.g. multi-scale structural similarity (MS-SSIM))
### Non-convergence, Convergence difficulty
the model parameters oscillate, destabilize
### Vanishing gradient because of too good discriminator
the discriminator gets too successful that the generator gradient vanishes and learns nothing
solution: [WGAN - Wasserstein distance](/generative_models/GAN_general.html#wgan-icml-2017)
### Image quality
* resolution
* noise
* high frequencey