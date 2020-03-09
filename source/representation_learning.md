# Representation Learning
usage: 
1. manipulate output of generative models
2. Transfer learning, embedding feature for classification / recognition / other task

## Latent Space
Latent Space of encoder
### Manipulation Process
input: unlabelled dataset to train encoder
1. Train encoder-decoder(e.g. AutoEncoder) with unlabelled dataset
2. Obtain average encoding of positive and negative inputs from labelled dataset
3. Get manipulation vector by taking difference
4. Manipulate new x_input along z_manipulate

## Embedding Models
#### word2vec
#### faceNet
## Generative models
### InfoGAN(NIPS)
[InfoGAN: Interpretable Representation Learning by Information Maximizing Generative Adversarial Nets](https://papers.nips.cc/paper/6399-infogan-interpretable-representation-learning-by-information-maximizing-generative-adversarial-nets.pdf)
* TODO!!