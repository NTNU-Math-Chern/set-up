## :fire_engine: Cuda & PyTorch

- [:fire\_engine: Cuda \& PyTorch](#fire_engine-cuda--pytorch)
  - [:teddy\_bear: Prerequisites](#teddy_bear-prerequisites)
  - [:car: Nvidia Driver](#car-nvidia-driver)
  - [:wrench: Cuda toolkit](#wrench-cuda-toolkit)
  - [:wrench: Multi-version Cuda installation and switching](#wrench-multi-version-cuda-installation-and-switching)
  - [:fire: PyTorch](#fire-pytorch)


### :teddy_bear: Prerequisites

```shell
gcc --version
conda --version
```

### :car: Nvidia Driver
```shell
nvidia-smi # skip this step if installed
```

check recommended drivers
```shell
sudo ubuntu-drivers devices
```
install specific driver (base on recommendation)
```shell
sudo apt install -y nvidia-driver-550
sudo reboot

# you might need to permit third-party driver with MOK
# if anything went wrong, remove all drivers and re-install
# sudo apt purge nvidia-*
# sudo apt autoremove

nvidia-smi
```

### :wrench: Cuda toolkit

```shell
nvcc --version # skip this step if installed
```

install cuda toolkit
```shell
sudo apt install -y nvidia-cuda-toolkit
sudo reboot

nvcc --version
```
### :wrench: Multi-version Cuda installation and switching

Download the version of CUDA you need from [here](https://developer.nvidia.com/cuda-toolkit-archive). It is recommended to install it using the **runfile** method. For example, to install CUDA 11.8, run:
```
wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_520.61.05_linux.run
sudo sh cuda_11.8.0_520.61.05_linux.run
```
Then switch it by
```shell
#CUDA 11.8 
export CUDA_HOME=/usr/local/cuda-11.8
export PATH=$CUDA_HOME/bin:$PATH
export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH
```

### :fire: PyTorch

We test it on conda base environment.
```shell
conda activate base
```

Install PyTorch with CUDA from [here](https://pytorch.org/get-started/locally/). If you follow the instructions above, you should be able to just install the lastest version.

```shell
# CUDA 12.4 (latest version)
pip3 install torch torchvision torchaudio
# CUDA 12.1
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
# CUDA 11.8
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

Run python and check if successfully installed.
```shell
import torch
print(torch.cuda.is_available())
# print(torch.cuda.get_device_name(0))
```

