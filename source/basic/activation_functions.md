# Activation Functions
## Sign
Fully connected hash layer
## Sigmoid
	saturated
## Tanh
	saturated
## ReLU
non-saturated
fast and solve gradient vanishing, but might cause gradient explosion
could be considered as dropout when input < 0
### Leaky ReLU
### PReLu
### ELU - Exponential Linear Uints  (2015)
[Fast and Accurate Deep Network Learning by Exponential Linear Units (ELUs)](https://arxiv.org/abs/1511.07289)
### SELU - Scaled Exponential Linear Unit (NIPS 2017)
[Self-Normalizing Neural Networks](https://arxiv.org/abs/1706.02515)  
α and λ are derived from the inputs.
For standard scaled inputs (mean 0, stddev 1), the values are α=1.6732~, λ=1.0507~
```math
    selu(x)= \lambda
\begin{cases}
    x                , & \text{if } x> 0\\
    \alpha e^x-\alpha, & \text{if } x\leq 0
\end{cases}

```


## Softmax
### A-Softmax
### L-Softmax
