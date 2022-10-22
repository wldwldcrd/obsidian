* GPU Usage: `nvidia-smi -l 1`
* Installation
``$ sudo apt-get update
``$ sudo apt-get upgrade
``$ sudo apt-get install python3-pip python3-dev
``$ sudo pip3 install tensorflow-gpu
* GPU Support
	* CUDA: https://developer.nvidia.com/cuda-downloads
	* cuDNN: https://developer.NVIDIA.com/cudnn
Установите библиотеку BLAS (в данном случае OpenBLAS), чтобы получить
поддержку быстрых операций с тензорами на CPU:
``$ sudo apt-get install build-essential cmake git unzip pkg-config libopenblas-dev liblapack-dev

``$ sudo apt-get install python-numpy python-scipy python- matplotlib python-yaml
``$ sudo apt-get install libhdf5-serial-dev python-h5py
``$ sudo apt-get install graphviz
``$ sudo pip install pydot-ng

# Cuda installation
Installing CUDA 10.1 on Ubuntu 20.04: https://medium.com/@stephengregory_69986/installing-cuda-10-1-on-ubuntu-20-04-e562a5e724a0
Fix repos with public keys https://chrisjean.com/fix-apt-get-update-the-following-signatures-couldnt-be-verified-because-the-public-key-is-not-available/