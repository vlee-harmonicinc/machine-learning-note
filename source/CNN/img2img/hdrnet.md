# hdrnet
[Deep Bilateral Learning for Real-Time Image Enhancement](https://groups.csail.mit.edu/graphics/hdrnet/data/hdrnet.pdf) by MIT, Google  
[Project](https://groups.csail.mit.edu/graphics/hdrnet/) | [tensorflow code](https://github.com/google/hdrnet)  
convert image to hdr image in real-time and mobile, inspired by bilateral grid processing and local affine color transforms.
### Image processing review
#### Bilateral Grid
[Real-time Edge-Aware Image Processing with the Bilateral Grid (SIGGRAPH 2007)](https://people.csail.mit.edu/sparis/publi/2007/siggraph/Chen_07_Bilateral_Grid.pdf)
x,y coordinates are augmented with third dimension which is a function of pixel's color
(gray 2D image -> 3D, color 2D image -> 5D)
**contributions**:
1. The bilateral grid: a new data structure that naturally enables edge-aware manipulation of image
2. Real-time bilateral filtering on GPU
3. Edge-aware algorithm: hdrnet introduce a number of real-time, edge-aware algorithms including edge-preserving painting, scattered data interpolation and local histogram equalization
#### Guided image filtering, ECCV 2010, TPAMI 2013
[Guided Image Filtering](http://kaiminghe.com/publications/eccv10guidedfilter.pdf)
#### Transform Recipes
[Transform Recipes for Efficient Cloud Photo Enhancement (ISGGRAPH 2015)](https://groups.csail.mit.edu/graphics/xform_recipes/data/xform_paper_sigasia2015.pdf)
Compression, image representation, image filter approximation
The task of computing the operator and fitting the recipe is offloaded to the cloud while the mobile device need only apply the recipe, thereby saving time and energy
[Bilateral Guided Upsampling (2016)](https://people.csail.mit.edu/hasinoff/pubs/ChenEtAl16-bgu.pdf)
### Contribution
targeting photographic transformation, which are often well-approximated with linear operation in bilateral space. Much faster than image-to-image transformation
![](img/hdrnet.png)
1. Slicing: perform prediction in low-resolution bilateral grid
   new slicing operator for deep learning that performs data-dependent lookup that reconstructs output image from 3D bilateral grid
2. Affine color transform: predict transformation rather than output directly. hdrnet is designed to learn, as intermediate representation, a local affine color transformation.
3. full-resolution loss: loss function used is evaluated at full resolution, causes the low-resolution transformation learn to be optimized for high-resolution