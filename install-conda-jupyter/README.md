## :cactus: Conda & Jupyter

- [:cactus: Conda \& Jupyter](#cactus-conda--jupyter)
  - [:snake: Anaconda](#snake-anaconda)
  - [:ringed\_planet: Jupyter notebook](#ringed_planet-jupyter-notebook)
  - [:telephone: Common commands](#telephone-common-commands)

### :snake: Anaconda

```shell
sudo apt install libgl1-mesa-glx libegl1-mesa libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxtst6
```

Download [Anaconda](https://www.anaconda.com/download) (skip registration). The file name should be something like `Anaconda3-20XX.XX.XX-Linux-x86_64.sh`, depends on your date and system.

```shell
cd Download # assuming you are at home

chmod +x Anaconda3-2024.10.1-Linux-x86_64.sh
./Anaconda3-2024.10.1-Linux-x86_64.sh
```

> You'll have to go through a long document, widen your terminal to go faster.

```shell
# in case you did not initialize conda
source ~/anaconda3/etc/profile.d/conda.sh
conda init
# disable default conda 
conda config --set auto_activate_base False
```

Re-open terminal, `(base)` should not be activated, run `conda activate base` to test conda.


### :ringed_planet: Jupyter notebook
Jupyter notebook should be installed with anaconda.

```
# set password
jupyter notebook password
# jupyter server 
jupyter notebook --ip 0.0.0.0 --port 1222 --no-browser
```

### :telephone: Common commands
```shell
# create new environment
conda create --name <VENV_NAME> python=<pythonVersion>
conda activate <VENV_NAMEE>
conda deactivate

# remove conda environment
conda env list
conda remove --name <VENV_NAMEE>  --all

# create jupyter kernel
conda activate <VENV_NAME>
(envName)$ pip install jupyter
(envName)$ ipython kernel install --name "<KERNEL_NAME>"

# remove jupyter kernel
jupyter kernelspec list
jupyter kernelspec remove <KERNEL_NAME>
```