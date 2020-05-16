# yolo34py + AlexeyAB的坑
yolo原作者pjreddie不再更新了，yolo v4 是[AlexeyAB的fork](https://github.com/AlexeyAB/darknet)出品。  
曾經用yolo34py API+ official libdarknet.so，但把darknet轉成AlexeyAB版本後會出錯，貌似用AlexeyAB的darknet.py也會出錯。  
原因是free_network 的API不同。  
解決辨法可以參考https://github.com/AlexeyAB/darknet/issues/3467  
2 approachs:
1. modify free_network, compile new so -> the darknet binary might be broken
[我改了原用的free_network成_free_network, 然後加free_network給yolo34py用](https://github.com/htleeab/darknet/tree/compatible_free_network_interface)
1. add api_free_network and change API(darknet.py or yolo34py) -> not compatible with pjreddie

object/pointer construction也跟official不同，比較難兼容...今後如果要用yolov4，大概直接拋棄pjreddie和yolo34py了

## YOLOv4 vs CenterNet
The CenterNet used in Yolo v4 is [NOT CenterNet: Objects as Points](https://github.com/AlexeyAB/darknet/issues/4130), which is the base of TTFNet.
darknet implement CenterNet: Triplet
So..currently there is not comparison between TTFNet/ CenterNet vs YOLOv4  
Looking for TTFNet implement to darknet [TTFnet: 10x Training Time Reduction · Issue #4690 · AlexeyAB/darknet](https://github.com/AlexeyAB/darknet/issues/4690)  

## Makefile

|                             | Description                                                                                                                                                                         |   |   |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| GPU                         | build with CUDA to accelerate by using GPU (CUDA should be in /usr/local/cuda)                                                                                                      |   |   |
| CUDNN                       |  to build with cuDNN v5-v7 to accelerate training by using GPU (cuDNN should be in /usr/local/cudnn)                                                                                |   |   |
| CUDNN_HALF                  | to build for mixed precision with Tensor Cores, speedup Detection 3x, Training 2x                                                                                                   |   |   |
| OPENCV                      | build with OpenCV 4.x/3.x/2.4.x - allows to detect on video files and video streams from network cameras or web-cams                                                                |   |   |
| AVX                         | speed up CPU with Advanced Vector Extensions (check support via `cat /proc/cpuinfo  \| grep avx`)                                                                                   |   |   |
| OPENMP                      | build with OpenMP support to accelerate Yolo by using multi-core CPU                                                                                                                |   |   |
| LIBSO                       | build a library darknet.so and binary runable file uselib that uses this library                                                                                                    |   |   |
| ZED_CAMERA, ZED_CAMERA_v2_8 | build a library with ZED-3D-camera support (should be ZED SDK installed)                                                                                                            |   |   |
| USE_CPP                     | the ability to compile in C++                                                                                                                                                       |   |   |
| DEBUG                       | build debug version of Yolo                                                                                                                                                         |   |   |
| ARCH                        | `compute_XX` refers to a PTX version. The `arch=` clause of the `-gencode=` command-line option to nvcc specifies the front-end compilation target and must always be a PTX version |   |   |

For my RTX 2070, using so lib for Python or C++ program: 

```
GPU=1
CUDNN=1
CUDNN_HALF=1
OPENCV=1
AVX=0
OPENMP=0
LIBSO=1
ZED_CAMERA=0 # ZED SDK 3.0 and above
ZED_CAMERA_v2_8=0 # ZED SDK 2.X

USE_CPP=0
DEBUG=0

ARCH= -gencode arch=compute_75,code=[sm_75,compute_75]
```
