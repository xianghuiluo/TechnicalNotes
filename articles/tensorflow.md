# TensorFlow GPU Installation on Ubuntu

While installing TensorFlow in a conda environment is easy as in [Install TensorFlow with pip](https://www.tensorflow.org/install/pip), a system-wide installation is much more involved.
This note walks through the steps to install a system-wide TensorFlow with GPU.\
At the time of this writing, the software requirements are
> NVIDIA® GPU drivers version 450.80.02 or higher.\
> CUDA® Toolkit 11.2.\
> cuDNN SDK 8.1.0.

## NVIDIA Driver
The first step is to install the NVIDIA driver. On more recently Ubuntu version, this is easy. Simply open "Software & Updates", navigate to the "Additional Drivers" tab and choose the latest NVIDIA driver as shown below.



## References
[Install TensorFlow with pip](https://www.tensorflow.org/install/pip)

[Back to Contents](../README.md)
