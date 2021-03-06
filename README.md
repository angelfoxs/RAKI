This program is an implementation of RAKI (Akcakaya et al 2019). If you use this code in one of your publications, please cite the following papers:

Akçakaya, M., Moeller, S., Weingärtner, S., & Uğurbil, K. (2019). Scan‐specific robust artificial‐neural‐networks for k‐space interpolation (RAKI) reconstruction: Database‐free deep learning for fast imaging. Magnetic resonance in medicine, 81(1), 439-453.

Zhang, C., Weingärtner, S., Moeller, S., Uğurbil, K., & Akçakaya, M. (2018, May). Fast GPU Implementation of a Scan-Specific Deep Learning Reconstruction for Accelerated Magnetic Resonance Imaging. In 2018 IEEE International Conference on Electro/Information Technology (EIT) (pp. 0399-0403). IEEE.

Zhang, C., Moeller, S., Weingärtner, S., Uğurbil, K., & Akçakaya, M. (2018, October). Accelerated Simultaneous Multi-Slice MRI using Subject-Specific Convolutional Neural Networks. In 2018 52nd Asilomar Conference on Signals, Systems, and Computers (pp. 1636-1640). IEEE.

06/14/2019: 3-layered RAKI available

In order to run this code, please set up a python 3.x environment with following packages installed:

1.Tensorflow & Tensorflow-gpu

2.scipy

3.numpy 

An NVIDIA GPU (with CUDA support) is recommended by not required. In the future, the accelerated versions will require NVIDIA GPU to complete RAKI reconstruction in seconds. 

To run a reconstruction, set network parameters at line 84-97:

#### Network Parameters ####
kernel_x_1 = 5

kernel_y_1 = 2


kernel_x_2 = 1

kernel_y_2 = 1


kernel_last_x = 3

kernel_last_y = 2


layer1_channels = 32 

layer2_channels = 8


MaxIteration = 3000

LearningRate = 3e-3

This default setting defines a 3-layered CNN, kernel sizes are: 5×2×n_c×32, 1×1×32×8, 3×2×8×R-1. The network parameters should be tuned individually for your input data. 

MaxIteration controls the number of epochs in network training. 

LearningRate is the learning rate for Adam optimizer.

#### Input/Output Data ####

inputData = 'rawdata.mat'

input_variable_name = 'kspace'

resultName = 'RAKI_recon'

recon_variable_name = 'kspace_recon'

These paramters tell where is the input data and where to store the reconstruction output.

inputData: a matlab mat file contains sub-sampled k-space data in complex single. ACS signal should be contained in the sub-sampled k-space data. 

input_variable_name: the variable name of input k-space data.

resultName: the name of output file. The output file will be matlab mat file.

recon_variable_name: the variable name of reconstructed k-space in output file.
