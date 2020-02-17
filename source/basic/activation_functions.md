# Activation Functions
Introduce non-linearity into the output of a neuron
## Step
```math
    step(x)= \lambda
\begin{cases}
    0              & \text{if } x< 0\\
    0.5            & \text{if } x= 0\\
    1              & \text{if } x\> 0
\end{cases}
```
could be used for hash layer
## Signum
```math
    sign(x)= \lambda
\begin{cases}
    -1             & \text{if } x< 0\\
    0              & \text{if } x= 0\\
    1              & \text{if } x\> 0
\end{cases}
```
could be used for hash layer
## Sigmoid
a.k.a. logistic  
saturated, monotonic  
derivative non-monotonic
```math
f(x)=\sigma(x)=\dfrac{1}{1+e^{-x}}
```
```math
f'(x)=f(x)(1-f(x))
```
## Tanh
saturated, monotonic  
derivative non-monotonic
```math
f(x)=tanh(x)=\dfrac{e^x-e^{-x}}{e^x+e^{-x}}
```
```math
f'(x)=1-f(x)^2
```
## ReLU
Rectified linear unit
non-saturated, monotonic, derivative monotonic
fast and solve gradient vanishing, but might cause gradient explosion
could be considered as dropout when input < 0
```math
f(x) = ReLU(x) = max(0,x) =
\begin{cases}
    0            , & \text{if } x\leq 0\\
    x             , & \text{if } x> 0
\end{cases}
```
```math
f'(x) = 
\begin{cases}
    0            , & \text{if } x\leq 0\\
    1             , & \text{if } x> 0
\end{cases}

```
### Leaky ReLU
```math
f(x) = 
\begin{cases}
    0.01x         , & \text{if } x\leq 0\\
    x             , & \text{if } x> 0
\end{cases}
```
### PReLU - Parametric ReLU
[Delving Deep into Rectifiers:Surpassing Human-Level Performance on ImageNet Classification](https://arxiv.org/abs/1502.01852)
```math
f(x) = 
\begin{cases}
    \alpha x      , & \text{if } x\leq 0\\
    x             , & \text{if } x> 0
\end{cases}
```
The momentum method is adopted when updating ``$`a_i`$``  
```math
\Delta\alpha_i := \mu\Delta\alpha_i+\epsilon\dfrac{\partial\varepsilon}{\partial\Delta\alpha_i}
```
where µ is the momentum and ``$`\epsilon`$`` is the learning rate  
### ELU - Exponential Linear Uints  (2015)
[Fast and Accurate Deep Network Learning by Exponential Linear Units (ELUs)](https://arxiv.org/abs/1511.07289)
```math
f(\alpha,x)=
\begin{cases}
    \alpha (e^x-1) , & \text{if } x\leq 0\\
    x              , & \text{if } x> 0
\end{cases}
```
### SELU - Scaled Exponential Linear Unit (NIPS 2017)
[Self-Normalizing Neural Networks](https://arxiv.org/abs/1706.02515)  
α and λ are derived from the inputs.
```math
    selu(x)= \lambda
\begin{cases}
    x                , & \text{if } x> 0\\
    \alpha e^x-\alpha, & \text{if } x\leq 0
\end{cases}
```
For standard scaled inputs (mean 0, stddev 1), the values are α=1.6732~, λ=1.0507~


## Softmax
mapping multiple neruals output to \[0,1]
could be used for classification (each output is probability)
```math
f_i(x)=\dfrac{e^{x_i}}{\Sigma^J_{j=1} e^{x_j}}
f_i'(y)=y_i/cdot(1-y_i)
```
where J is the number of neruals in the layer
### A-Softmax
### L-Softmax
