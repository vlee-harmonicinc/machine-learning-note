# Support-vector machines - SVM
Support-vector machines are supervised learning models with associated learning algorithms that analyze data.

Maximize the margin
Find hyperplane satisfying
```math
\vec{w}\cdot\vec{x}-b=0
```
### Hard Margin
```math
\vec{w}\cdot\vec{x}_i-b\geq 1  \text{ if } y_i=1 \\  \text{or} \\
\vec{w}\cdot\vec{x}_i-b\leq -1  \text{ if } y_i=-1
```
rewritten as
```math
y_i(\vec{w}\cdot\vec{x}_i-b)\geq 1
```

### Soft-margin

### Kernel Trick
In addition to performing linear classification, SVMs can efficiently perform a non-linear classification using what is called the kernel trick, implicitly mapping their inputs into high-dimensional feature spaces.  
Could imagine using "kernel" to twist the plane, so that there is a linear cutting that could maximize the margin  
![](img/svm_kernel_trick.png)
see also: [SVM with polynomial kernel visualization](https://www.youtube.com/watch?v=3liCbRZPrZA)
## kernal
### Linear
### Gaussian (radial basis function) RBF
```math
k(x,y)=e^{-\dfrac{||x-y||^2}{2\sigma^2}}\\
k(x_i, x_j)=e^{-\gamma||x_i-x_j||^2}
```
it is the most used non-linear kernel, because the number of parameters is small hence faster speed with good result
### Polynomial
```math


```
### Sigmoid

## SVM application
### SVR - Support vector regression
### SVC - Support vector classification
Simply using the regression result line as classification boundary