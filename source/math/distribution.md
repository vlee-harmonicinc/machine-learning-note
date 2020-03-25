# Discrete Distribution

## Binomial Distribution
```math
Pr(X=x)=\binom{n}{x}p^x{(1-p)}^{n-x}
```
### Bernoulli Distribution
A Bernoulli distribution is a special case of binomial distribution. Specifically, when n=1, i.e. x only could be 0 or 1, the binomial distribution becomes Bernoulli distribution.
## Geometric Distribution
The geometric distribution gives the probability that the first occurrence of success requires k independent trials, each with success probability p. If the probability of success on each trial is p, then the probability that the kth trial (out of k trials) is the first success is
```math
Pr(X=x)=(1-p)^{x-1}p
```
## Poisson Distribution
Poisson distribution is a discrete probability distribution that expresses the probability of a given number of events occurring in a fixed interval of time.
```math
Pr(X=x)=\frac{\lambda^x e^{-\lambda}}{x!}, \\
\lambda = E(X) = Var(X)
```
# Continuous Distribution
## Uniform Distribution
```math
Pr(X=x) = \frac{1}{n}
```
## Normal Distribution
i.e. Gaussian distribution  
```math
Pr(X=x)={\frac {1}{\sigma {\sqrt {2\pi }}}}e^{-{\frac {1}{2}}\left({\frac {x-\mu }{\sigma }}\right)^{2}}
```
## Exponential Distribution