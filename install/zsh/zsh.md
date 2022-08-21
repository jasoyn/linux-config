# ZSH

## 1 Basics

```sh
# 1. tmux
sudo apt install tmux -y

# 2. zsh
sudo apt install zsh -y

# 2.1. oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 2 Advanced Packages

```sh
# 2.1 zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# 2.2 zsh-vi-mode
git clone https://github.com/jeffreytse/zsh-vi-mode $ZSH_CUSTOM/plugins/zsh-vi-mode

# 2.3 zsh-auto-suggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Add the following to `~/.zshrc`:

```sh
plugins=( 
    zsh-vi-mode
    zsh-syntax-highlighting
    zsh-autosuggestions
)
```

## 3 Configuration

Correct escape sequence and some aliases:

```sh
# zsh-vi-mode escape sequence
ZVM_VI_INSERT_ESCAPE_BINDKEY=fd
# Uncomment line below
source $ZSH/oh-my-zsh.sh
# VS Code
export PATH=$PATH:"/mnt/c/Users/albert/AppData/Local/Programs/Microsoft VS Code/bin"

# Alias
alias te="tar --extract --file"
alias md="mkdir -p"
alias gd="cd .."
alias oc="code ."
```
