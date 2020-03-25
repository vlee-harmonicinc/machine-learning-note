# Variation Inference
## Background: Bayesian Inference
[Bayesian inference - Wikipedia](https://en.wikipedia.org/wiki/Bayesian_inference)  
```math
P(H|E) = \frac{P(E|H)\dot P(H)}{P(E)}
```
## Variation Bayesian method
[(NIPS 2016 Tutorial)Variational Inference: Foundations and Modern Methods](https://media.nips.cc/Conferences/2016/Slides/6199-Slides.pdf)  
A probabilistic model is a joint distribution of hidden variables z and observed variables x,
```math
p(z, x)
```
Inference about the unknowns is through the posterior, the conditional distribution of the hidden variables given the observations 
```math
p(z|x) = \frac{p(z,x)}{p(x)}
```
For most interesting models, the denominator is not tractable. We appeal to **approximate posterior inference**.


# Evidence Lower BOund (ELBO)