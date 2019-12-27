# Support-vector machines - SVM
Support-vector machines are supervised learning models with associated learning algorithms that analyze data.

Maximize the margin

### Kernel Trick
In addition to performing linear classification, SVMs can efficiently perform a non-linear classification using what is called the kernel trick, implicitly mapping their inputs into high-dimensional feature spaces.  
Could imagine using "kernel" to twist the plane, so that there is a linear cutting that could maximize the margin  
![](img/svm_kernel_trick.png)
see also: [SVM with polynomial kernel visualization](https://www.youtube.com/watch?v=3liCbRZPrZA)
## kernal
### Linear
### Gaussian (radial basis function) RBF
```math
k(x,y)=exp(-\dfrac{||x-y||^2}{2\sigma^2})\\
k(x_i, x_j)=exp(-\gamma||x_i-x_j||^2)
```
it is the most used non-linear kernel, because the number of parameters is small hence faster speed with good result
### Polynomial
### Sigmoid

## SVM application
### SVR - Support vector regression
### SVC - Support vector classification
Simply using the regression result line as classification boundary