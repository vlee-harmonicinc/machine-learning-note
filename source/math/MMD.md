# Maximum Mean Discrepancy (MMD) 
A measure of the difference between two probability distributions from their samples. 

```math
MMD(P,Q)= \overbrace {\sup_{f \in H}}^{\text{least upper bound over test functions }f \in H}
          \overbrace{\parallel \mathbb{E}_{X\sim P}[f(X)]-\mathbb{E}_{Y\sim Q}[f(Y)] \parallel}^{\text{mean discrepancy}}
```
 
* compares distributions without initially estimating their density functions.
* applied in [KID](../GAN/metrics.md#kernel-inception-distance-kid) to measure GAN convergence
* applied in many transfer learning models as regularization/ loss to encourage the latent representation to be invariant across different domains
