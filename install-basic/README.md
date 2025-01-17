## :gear: Basic set-up

Update system
```shell
sudo apt update
sudo apt upgrade
```

Build tools
```shell
sudo apt instsall -y build-essential cmake gdb

# commonly used dependencies
sudo apt install -y libeigen3-dev libboost-all-dev libomp-dev
# formatting
sudo apt install -y clang-format
```

Python
```shell
sudo apt install -y python3 python3-pip 
sudo apt install -y python3-dev python3-venv
# ignore the following command if you want to use python 2
sudo apt install -y python-is-python3

# commonly used packages
pip install numpy matplotlib pandas scipy
# formatting
pip install ruff
```

VSCode
```shell
sudo snap install code --classic
```

Git
```shell
sudo apt install -y git

git config --global user.name "ChernLab"
git config --global user.email "chernlab.math.ntnu@gmail.com"
```

Others
```shell
sudo apt install -y vim net-tools
```

Check important installs
```shell
gcc --version
g++ --version
make --version
cmake --version
python --version
pip --version
code --version
git --version
```