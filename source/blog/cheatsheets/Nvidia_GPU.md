# Nvidia GPU
*GPGPU*: General-purpose computing on graphics processing units
*Nvidia*: Company that design graphics processing units (GPUs) for the gaming and professional markets. Nvidia GPU have better ecosystem for Machine Learning. 
## Monitor GPU
`nvcc --version` # check CUDA version with nvcc
`nvidia-smi`  
`watch -n 1 nvidia-smi`  

## GPU Summary Table
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vSgr6g0R2M5IRIJbgU71Xxva89bo5mQ1u0ZVgVpQC_ZVEZOE27pI-ck2ygIYcmHMc13M4ODbGAzEG6T/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false"></iframe>

[Google Spreadsheets](https://docs.google.com/spreadsheets/d/1AAe7gB0vfOtU_RMjE_WNcjrSmB6_LLgUIPj9cfR3KFw/edit?usp=sharing)  

* Processing Power: GeForce stat from [wiki/GeForce_10_series](https://en.wikipedia.org/wiki/GeForce_10_series),  [wiki/GeForce_20_series](https://en.wikipedia.org/wiki/GeForce_20_series), Tesla stat from Nvidia  
* **tensor precision** support by Tensor Core, from some Volta and newer architecture FP16 matrix math with FP16 accumulation, x8 speed up. Stat of tensor precision mostly come from Nvidia, such as [Turing Whitepaper](https://www.nvidia.com/content/dam/en-zz/Solutions/design-visualization/technologies/turing-architecture/NVIDIA-Turing-Architecture-Whitepaper.pdf). 
* half precision that slower than single precision consider as not supported.
* Google Cloud Platform(GCP) [GPUs Pricing](https://cloud.google.com/compute/gpus-pricing)
![](https://www.nvidia.com/content/dam/en-zz/Solutions/Data-Center/tesla-t4/Turing-Tensor-Core_30fps_FINAL_736x414.gif)

### Precision
Lower Precision could speed up training and inference time. 
**Precision support matrix**

|             | Ampere                                       | Turing                 | Volta                  |
|-------------|----------------------------------------------|------------------------|------------------------|
| Tensor Core | FP64, TF32, bfloat16, FP16, INT8, INT4, INT1 | FP16, INT8, INT4, INT1 | FP16                   |
| CUDA® Core  | FP64, FP32, FP16, bfloat16, INT8             | FP64, FP32, FP16, INT8 | FP64, FP32, FP16, INT8 |

TF datatype preserve bits for exponent (lossing precision):
![](https://devblogs.nvidia.com/wp-content/uploads/2020/05/TensorFloat32-TF32.jpg) from [NVIDIA Ampere Architecture In-Depth](https://devblogs.nvidia.com/nvidia-ampere-architecture-in-depth/)
To handle the loss of precision, 
1. scaling loss and gradient
1. mixed precision (multiply as FP16/TF32, add and save as FP32)
1. low precision for inference (e.g. INT4, INT8). 
For more detail of inference optimization, see [tensorRT](#tensorrt)
For more detail of training optimization, see [AMP](#amp)
## ==Software==

## CUDA, Compute Unified Device Architecture
API for Nvidia’s GPU  
Some SOTA papers have its own CUDA code to implement its novel idea, such as deformable convolution in CNN, optical flow wrapper in frame interpolation papers. 
## nvcc, **Nv**idia **C**UDA **C**ompiler  
CUDA (c++) code compiler, see [nvcc C++ Language Support ](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#c-cplusplus-language-support)

## cuDNN, **CU**DA **D**eep **N**eural **N**etwork library
GPU-accelerated library for deep neural nets built using CUDA. cuDNN provides highly tuned implementations for standard routines such as *forward and backward convolution, pooling, normalization, and activation layers*. Mainly for neural network framework developer(Caffe, torch etc).  
`torch.backends.cudnn.benchmark = True` which always appear in pyTorch code take advantage of cuDNN to speed up when the model is unchanged.
	
## TensorRT
Tensor **R**un**T**ime  
NVIDIA TensorRT™ is an **SDK for high-performance deep learning inference**. It includes a deep learning inference optimizer and runtime that delivers low latency and high-throughput for deep learning inference applications.  
Some training frameworks such as TensorFlow have integrated TensorRT so that it can be used to accelerate inference within the framework. Alternatively, TensorRT can be used as a library within a user application. It includes parsers for importing existing models from Caffe, ONNX, or TensorFlow, and C++ and Python APIs for building models programmatically.  
[TensorRT Developer Guide](https://docs.nvidia.com/deeplearning/sdk/tensorrt-developer-guide/index.html)
### Deploy Model with TensorRT
1. prepared a pre-trained network with original neural network framework (don’t train on tensorRT)
1. Creating a TensorRT network definition from your model
    1. convert model to TensorRT compatable format (e.g. pyTorch to ONNX, [torch2trt](https://github.com/NVIDIA-AI-IOT/torch2trt))
    1. define custom layer if TensorRT have not [build-in support](https://docs.nvidia.com/deeplearning/sdk/tensorrt-support-matrix/index.html), e.g. deformable convolution (in cuda)
1. Invoking the TensorRT builder to create an optimized runtime engine from the network
    1. import custom layer
    1. calibration: for INT8 precision, calibrate via determine the dynamic range of intermediate activations, and hence the appropriate scaling factors for quantization
1. Serializing and deserializing the engine so that it can be rapidly recreated at runtime
1. Feeding the engine with data to perform inference with TensorRT C++/Python lib

### AMP
[Automatic Mixed Precision](https://developer.nvidia.com/automatic-mixed-precision)

### Nvidia Documents
[CUDA C++ Programing Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html)  
[CUDA C++ Best Practices Guide](https://docs.nvidia.com/cuda/cuda-c-best-practices-guide/index.html)
[CUDA Math API](https://docs.nvidia.com/cuda/cuda-math-api/modules.html)
[Mixed Precision Training](https://docs.nvidia.com/deeplearning/performance/mixed-precision-training/index.html)  
#### [An Even Easier Introduction to CUDA](https://devblogs.nvidia.com/even-easier-introduction-cuda/)  
1. Add Specifier to the code that run on GPU  
    __global__: runs on the GPU and can be called from CPU code, kernel  
    __device__: runs on the GPU and can be called from GPU code, device code  
    __host__: runs on the CPU and can be called from CPU code, host code  
1. Memory Allocation in CUDA
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
