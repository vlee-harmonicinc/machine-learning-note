# UNIT series
## UNIT (NIPS 2017)
[Unsupervised Image-to-Image Translation Networks](https://arxiv.org/abs/1703.00848) by Nvidia  
Seperate the generator of GAN into encoder+decoder pairs, just like VAE.  
**Shared-latent space** constraint implies the cycle-consistency constraint.  
VAE + GAN + share weight of last layer of E1 and E2; also share the first layer of G1, G2  
![](img/UNIT.png)  
Cycle-consistency is not necessary for this task, however, preformance: proposed(UNIT-shared latent space + cycle-consistency) > cycleGAN > shared latent space (VAE-GAN)  
comparing with cycleGAN, it learn shape better.  
## MUNIT (ECCV 2018)
[Multimodal Unsupervised Image-to-Image Translation](https://arxiv.org/abs/1804.04732)  
1. seperate latent code into content code and style code, learn from swapping attribute code  
1. style is embedded in hidden layer of generator  
![](img/MUNIT.png)
## DRIT (ECCV 2018)
[Diverse Image-to-Image Translation via Disentangled Representations](https://arxiv.org/abs/1808.00948)  
[Project](http://vllab.ucmerced.edu/hylee/DRIT_pp/) | [Pytorch 0.4.0](https://github.com/HsinYingLee/DRIT/)  
1. concurrent works of MUNIT, style code in MUNIT~attribute code in DRIT  
1. keep weight sharing of UNIT
1. add content adversarial loss to force content generator produce encoding that could not be distingished, same concept of [Transfer Learning/DANN](/transfer_learning/index.html#dann-nips-2014)
### DRIT++ (IJCV Journal extension for ECCV 2018)
[DRIT++: Diverse Image-to-Image Translation via Disentangled Representations](https://arxiv.org/abs/1905.01270) 
1. mode-seeking regularization for improving sample diversity [Mode Seeking GAN](GAN_general.html#mode-seeking-gan-cvpr-2019)
1. add one-hot domain code