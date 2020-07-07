# Kullback–Leibler divergence
called relative entropy, a measure of how one probability distribution is different from a second, reference probability distribution.
```math
D_{KL}(P \parallel Q)    & =\sum^n_{i=1}P(i)\ln(\dfrac{P(i)}{Q(i)}) \\
                         & =\int _{{-\infty }}^{\infty }p(x)\ln {\frac  {p(x)}{q(x)}} {\rm {d}}x
```
* always non-negative `$D_{KL}(P \parallel Q) \geq 0$`
* asymmetry `$D_{{{\mathrm  {KL}}}}(P \parallel Q)\neq D_{{{\mathrm  {KL}}}}(Q\|P)$`
* `$D_{KL}(P \parallel Q) =0 \iff P=Q$`
