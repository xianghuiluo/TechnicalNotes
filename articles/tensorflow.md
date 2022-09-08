# TensorFlow GPU Installation on Ubuntu

While installing TensorFlow in a conda environment is easy as in [Install TensorFlow with pip](https://www.tensorflow.org/install/pip), a system-wide installation is much more involved.
This note walks through the steps to install a system-wide TensorFlow with GPU.\
At the time of this writing, the software requirements are
> NVIDIA® GPU drivers version 450.80.02 or higher.\
> CUDA® Toolkit 11.2.\
> cuDNN SDK 8.1.0.

## Step 1 - NVIDIA Driver
The first step is to install the NVIDIA driver. On more recently Ubuntu version, this is easy. Simply open "Software & Updates", navigate to the "Additional Drivers" tab and choose the latest NVIDIA driver as shown below.
![Image](../data/nvidia-driver.png)

## Step 2 - CUDA
Download cuda_11.2.0_460.27.04_linux.run from [https://developer.nvidia.com/cuda-toolkit-archive](https://developer.nvidia.com/cuda-toolkit-archive). Install CUDA by running the file. Since the NVIDIA driver is already installed in the above step, choose not to install driver during the installation process as shown below.
![Image](../data/tf-cuda-1.png)
![Image](../data/tf-cuda-2.png)

## Step 3 - cuDNN

## Step 4 - TensorFlow

## References
[Install TensorFlow with pip](https://www.tensorflow.org/install/pip)

[Back to Contents](../README.md)
