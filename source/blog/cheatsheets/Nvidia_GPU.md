# Nvidia GPU
*GPGPU*: General-purpose computing on graphics processing units
*Nvidia*: Company that design graphics processing units (GPUs) for the gaming and professional markets. Nvidia GPU have better ecosystem for Machine Learning. 
## Monitoring
`nvidia-smi`  
`watch -n 1 nvidia-smi`

## GPU Summary Table
[Google Spreadsheets](https://docs.google.com/spreadsheets/d/1AAe7gB0vfOtU_RMjE_WNcjrSmB6_LLgUIPj9cfR3KFw/edit?usp=sharing)

## Mixed precision
[Mixed Precision Training](https://docs.nvidia.com/deeplearning/performance/mixed-precision-training/index.html)  
With half precision, it could lower memory consumsion and speed up
* half precision that slower than single precision consider as not supported.
* tensor precision stat (1:8) provided by Nvidia [Turing Whitepaper](https://www.nvidia.com/content/dam/en-zz/Solutions/design-visualization/technologies/turing-architecture/NVIDIA-Turing-Architecture-Whitepaper.pdf), other wiki

With Tensor core (4x4 matrix core) +  with FP16 Accumulate (TensorRT), theologically x8 speed up (usually x2~3 because of memory bound)
Processing Power: GeForce stat from [wiki/GeForce_10_series](https://en.wikipedia.org/wiki/GeForce_10_series),  [wiki/GeForce_20_series](https://en.wikipedia.org/wiki/GeForce_20_series), Tesla stat from Nvidia  
Google Cloud Platform(GCP): https://cloud.google.com/compute/gpus-pricing

# CUDA
Compute Unified Device Architecture  
Some SOTA papers have its own CUDA code to implement its novel idea, such as deformable convolution, optical flow wrapper. So better understand some basic CUDA programming.  
[An Even Easier Introduction to CUDA](https://devblogs.nvidia.com/even-easier-introduction-cuda/)  
1. Add Specifier to the code that run on GPU
    __global__: runs on the GPU and can be called from CPU code, kernel
    __device__: runs on the GPU and can be called from GPU code, device code
    __host__: runs on the CPU and can be called from CPU code, host code
1. Memory Allocation in CUDA
    `cudaMallocManaged, cudaFree`
1. caller add execution configuration <<<numBlocks, blockSize>>>
    numBlocks: the number of thread block
    blockSize: the number of thread in thread block, suggest to be multiple of 32
1. in the kernel, assign index for parallel computation
    value|description
    ---|---
    `gridDim.x`|the number of blocks in the grid
    `blockIdx.x`|the index of the current thread block in the grid
    `blockDim.x`| the number of threads in the block
    `threadIdx.x`| the index of the current thread within its block
### Documents
[CUDA C++ Programing Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html)  
[CUDA C++ Best Practices Guide](https://docs.nvidia.com/cuda/cuda-c-best-practices-guide/index.html)
[CUDA Math API](https://docs.nvidia.com/cuda/cuda-math-api/modules.html)
#### Datatype: half vs half2
half2 structures store two half values in the space of a single 32-bit word, as the bottom of Figure 1 shows.

## cuDNN
The NVIDIA CUDA® Deep Neural Network library (cuDNN) is a GPU-accelerated library of primitives for deep neural networks. cuDNN provides highly tuned implementations for standard routines such as *forward and backward convolution, pooling, normalization, and activation layers*.

## TensorRT
NVIDIA TensorRT™ is an **SDK for high-performance deep learning inference**. It includes a deep learning inference optimizer and runtime that delivers low latency and high-throughput for deep learning inference applications.
TensorRT provides **INT8 and FP16 optimizations** for production deployments of deep learning inference applications. Reduced precision inference significantly reduces application latency, which is a requirement for many real-time services, auto and embedded applications.

