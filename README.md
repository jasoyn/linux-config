# Post installation for Ubuntu 22.04

## Terminal related things

For servers and workstations.

###  Basic packages

```sh
# 0. tmux
sudo apt install tmux -y
# 1. zsh
sudo apt install zsh -y
# 1.1. oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Wait for installation to finish and press `enter` when asked `Do you want to change your default shell to zsh? [Y/n]`.
    

### Advanced packages

```sh
# 1.2. zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
# 1.3. zsh-vi-mode
git clone https://github.com/jeffreytse/zsh-vi-mode $ZSH_CUSTOM/plugins/zsh-vi-mode

# 2. SpaceVim
sudo apt purge vim; sudo apt install neovim -y
curl -sLf https://spacevim.org/install.sh | bash
```

### Configuration

Add this to `~/.zshrc`:

```sh
plugins=( 
    # other plugins...
    zsh-autosuggestions
    zsh-vi-mode
)

# Only changing the escape key to `jk` in insert mode, we still
# keep using the default keybindings `^[` in other modes
ZVM_VI_INSERT_ESCAPE_BINDKEY=fd
```

and this to `~/.SpaceVim.d/init.toml` using `SPC f v d`:

```toml
[[layers]]
  name = "colorscheme"

[options]
  colorscheme = "onedark"

[options]
    escape_key_binding = 'fd'
    relativenumber=false
    windows_leader = ''
    
[[layers]]
  name = "lang#fortran"

[[layers]]
  name = "lang#python"
```

relaunch SpaceVim twice.
