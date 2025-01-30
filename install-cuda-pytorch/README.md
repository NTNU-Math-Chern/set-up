## :fire_engine: Cuda & PyTorch

- [:fire\_engine: Cuda \& PyTorch](#fire_engine-cuda--pytorch)
  - [:teddy\_bear: Prerequisites](#teddy_bear-prerequisites)
  - [:car: Nvidia Driver](#car-nvidia-driver)
  - [:wrench: Cuda toolkit](#wrench-cuda-toolkit)
  - [:bricks: Multi-version CUDA](#bricks-multi-version-cuda)
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

> This CUDA version you see here is the maximum version supported by the driver.

### :wrench: Cuda toolkit

```shell
nvcc --version # skip this step if installed
```

Since we want to use PyTorch, first check the latest version (or any version you want) [here](https://pytorch.org/get-started/locally/).
Then install cuda toolkit [here](https://developer.nvidia.com/cuda-toolkit-archive), we use CUDA 12.6. 
It is recommended to install it using the **runfile** method, note that don't select install driver again.
```shell
wget https://developer.download.nvidia.com/compute/cuda/12.6.3/local_installers/cuda_12.6.3_560.35.05_linux.run
sudo sh cuda_12.6.3_560.35.05_linux.run
```
Add CUDA path (or add it to your shell configuration file, we will give instructions [below](#bricks-multi-version-cuda)).
```shell
export CUDA_HOME=/usr/local/cuda-12.6
export PATH=$CUDA_HOME/bin:$PATH
export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH

nvcc --version
```

> This CUDA version you see here is the version we are using.

### :bricks: Multi-version CUDA
For example, we install CUDA 11.8.
It is recommended to install it using the **runfile** method, note that don't select install driver again.
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

**Switch CUDA**

For simplicity, we define functions to switch CUDA version more easily. Put the following script in your shell configuration file (e.g., default `vim ~/.bashrc` or we use `vim ~/.zshrc`).

```
# Default CUDA version
export CUDA_DEFAULT_VERSION=12.6

# Fuction to check available CUDA versions
cuda_list() {
    ls /usr/local | grep cuda-
}

# Function to switch CUDA versions
cuda_switch() {
    if [ -z "$1" ]; then
        echo "Usage: switch_cuda <version>"
        return 1
    fi
    export CUDA_HOME="/usr/local/cuda-$1"
    export PATH="$CUDA_HOME/bin:$PATH"
    export LD_LIBRARY_PATH="$CUDA_HOME/lib64:$LD_LIBRARY_PATH"

    # Print only if NOT running in silent mode
    if [ "$2" != "silent" ]; then
        echo "Switch to CUDA $1"
    fi
}

# Set default CUDA version at startup
cuda_switch $CUDA_DEFAULT_VERSION silent
```

Restart shell or reload shell by `source ~/.bashrc`. We added two functions:
- `cuda_list`: Print available CUDA versions in `/usr/local/`.
- `cuda_switch <VERSION>`: Switch to CUDA `<VERSION>`.

### :fire: PyTorch

We test it on conda base environment.
```shell
conda activate base
```

Install PyTorch with CUDA from [here](https://pytorch.org/get-started/locally/). If you follow the instructions above, you should install CUDA 12.6 version.

```shell
# CUDA 12.6 
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126
# CUDA 11.8
# pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

Run python and check if successfully installed.
```python
import torch
print(torch.version.cuda) # 12.6
print(torch.cuda.is_available()) # true
print(torch.cuda.get_device_name(0))
```

