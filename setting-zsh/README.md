## :battery: Oh My Zsh

```shell
sudo apt install -y zsh curl vim
chsh -s $(which zsh)
echo $SHELL # check current shell
```

Might need to log out and back in for `zsh` to apply.

```shell
# oh my zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
# autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
# syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
# theme powerlevel10k
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```

Change configuration by `vim ~/.zshrc` with 
```shell
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```
`vim` cheat sheet: 
- enter edit mode by `i`
- leave edit mode by `esc`
- save by `:w`
- quit by `:q`

Reload shell by `source ~/.zshrc` and configure the theme.

**Conda**

Might need to initialize `conda` for `zsh`.

```shell
# in case you did not initialize conda
source ~/anaconda3/etc/profile.d/conda.sh
conda init zsh
# disable default conda 
conda config --set auto_activate_base False
```
