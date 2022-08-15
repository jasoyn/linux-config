# Post installation for Ubuntu 22.04

## 1. Terminal related things

For servers and workstations.

### 1.1 Basic packages

```sh
# 0. tmux
sudo apt install tmux -y
# 1. zsh
sudo apt install zsh -y
# 1.1. oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Wait for installation to finish and press `enter` when asked `Do you want to change your default shell to zsh? [Y/n]`.
    

### 1.2 Advanced packages

```sh
# 1.2. zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
# 1.3. zsh-vi-mode
git clone https://github.com/jeffreytse/zsh-vi-mode $ZSH_CUSTOM/plugins/zsh-vi-mode

# 2. SpaceVim
sudo apt purge vim; sudo apt install neovim -y
curl -sLf https://spacevim.org/install.sh | bash
```

### 1.3 Configuration

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

## 2. VS Code

### 2.1 Extensions to install (in Remote Mode)

1. Vim, VSpaceCode (configure automatically!)
2. Remote WSL, SSH
3. Markdown Preview Enhanced, Markdown All in One
4. Python
5. Quarto, Pandoc Citer
6. git history, GitLens, etc.

### 2.2 Configuration

1. Vim escape sequence (`settings.json`)

    ```json
    // Vim key settings 
    "vim.insertModeKeyBindings": [
        {
            "before": [
                "f", "d"
            ],
            "after": [
                "<Esc>"
            ]
        }
    ],
    ```

2. Markdown snippets and autocompletion

    ```json
    "[markdown]": {
      "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": false
      }
    }
    ```

## 3. LaTeX, Pandoc, R, Quarto, Markdown

```sh
# 1. LaTeX
sudo apt install markdown texlive-full -y
# 2. pandoc
cd $HOME/Downloads
wget https://github.com/jgm/pandoc/releases/download/2.19/pandoc-2.19-1-amd64.deb  # Pandoc 2.19
sudo apt install ./pandoc-2.19-1-amd64.deb
# 3. pandoc-crossref
wget https://github.com/lierdakil/pandoc-crossref/releases/download/v0.3.13.0/pandoc-crossref-Linux.tar.xz  # Pandoc-crossref 0.3.13.0
tar -xf pandoc-crossref-Linux.tar.xz
sudo mv pandoc-crossref /usr/local/bin/
sudo chmod a+x /usr/local/bin/pandoc-crossref
# 4. R
sudo apt install r-base -y
# 5. Quarto
sudo wget https://github.com/quarto-dev/quarto-cli/releases/download/v1.0.38/quarto-1.0.38-linux-amd64.deb
sudo apt install ./quarto-1.0.38-linux-amd64.deb
```

## 4. CFD related things

### 4.1 OpenFOAM, hyStrath

### 4.2 SU2

## 5. Project-ID Database