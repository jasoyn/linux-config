## ZSH Configuration

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
alias upg="sudo apt update && sudo apt upgrade -y"
alias yay="sudo apt install -y"
```
