# CycleGAN + growing
Note: [CycleGAN], [progressive GAN]
With limited GPU, is it possible to train a low-resolution cycleGAN, then drop the second generator-discriminator pair to free memory, and use progressive GAN/ pix2pixHD growing method to increase resolution?
Or even add progressive growing into CycleGAN like [Gapeng want to try](https://zhuanlan.zhihu.com/p/30637133)
## TODO experiments
train cycleGAN in patch manner
train cycleGAN with small / middle size
apply super-resolution on above output
pretrained small cycleGAN + pix2pixHD growing
pretrained small cycleGAN + progressive GAN growing
- 26/03/2020