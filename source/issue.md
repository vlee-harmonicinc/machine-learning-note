# Issues
## Overfitting
solutions: validation set & early stopping, weight regularization, dropout  
## Gradient Vanishing
solutions:  
1. reduce number of layers
2. ReLU instead of sigmod/ tanh
3. skip connection, e.g. U-net
## Gradient Explosion
solutions:
1. reduce number of layers
2. gradient clipping
3. weight regularization
4. skip connection, e.g. Residual module
## Loss divergent
## Internal Covariate Shift
reason: input of layer/activation is not i.i.d. when there is a change in the input distribution to our network. When the input distribution changes, hidden layers try to learn to adapt to the new distribution  
cause problem: unstable learning  
good solutions: Normalization
bad solution: lower learning rate
## Latent Space
better be independent and follow () distribution so that it could be manipulated