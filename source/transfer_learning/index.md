# Transfer Learning
## DANN (NIPS 2014)
[Domain-Adversarial Neural Networks](https://arxiv.org/abs/1412.4446)
[Domain-Adversarial Training of Neural Networks (JMLR 2016)](https://arxiv.org/abs/1505.07818)
![](img/domain-adversarial_training.png)
|module           | function|
|--|--|
|feature extractor| model to be transfered and tunned|
|label predictor  | predict output|
|doman classifier | identify if target input within source input domain. If clasifier distinguish as new domain, high loss-> force feature extractor learn to mix 2 domain|

Example: Given labelled grey-scaled MNIST and unlabeled color MNIST, want to train model for classifier of color MNIST without labelling color MNIST.
