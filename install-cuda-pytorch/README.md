## :fire_engine: Cuda & PyTorch

- [:fire\_engine: Cuda \& PyTorch](#fire_engine-cuda--pytorch)
  - [:teddy\_bear: Prerequisites](#teddy_bear-prerequisites)
  - [:car: Nvidia Driver](#car-nvidia-driver)
  - [:wrench: Cuda toolkit](#wrench-cuda-toolkit)
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

