# Representation Learning
Usage: 
1. Manipulate output of generative models
2. Transfer learning, embedding feature for other task (e.g. faceNet for face recognition, word2vec for NLP)

## Latent Space
Latent Space of encoder
### Manipulation Process
input: unlabelled dataset to train encoder
1. Train encoder-decoder(e.g. AutoEncoder) with unlabelled dataset
2. Obtain average encoding of positive and negative inputs from labelled dataset
3. Get manipulation vector by taking difference
4. Manipulate new x_input along z_manipulate

## Embedding Models
#### autoencoder
> The quintessential example of a representation learning algorithm is theau-toencoder. An autoencoder is the combination of anencoderfunction, whichconverts the input data into a diﬀerent representation, and adecoderfunction,which converts the new representation back into the original format. Autoencodersare trained to preserve as much information as possible when an input is runthrough the encoder and then the decoder, but they are also trained to make thenew representation have various nice properties. Diﬀerent kinds of autoencodersaim to achieve diﬀerent kinds of properties. --Deep Learning
#### word2vec
#### faceNet
## Generative models
### InfoGAN(NIPS 2016)
[generative_models/GAN.md#InfoGAN(NIPS 2016)](generative_models/GAN#infogan-nips-2016)
