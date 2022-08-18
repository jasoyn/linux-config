# Linux Configuration

This is a collection of my complete Linux configuration for computational fluid dynamics and software development on
WSL2.

| Name | Install | Config |
| ---  |  :------: | :------: |
| WSL terminal | | [&#11044;](config/wsl-terminal/wsl-terminal.md)|
| zsh | [&#11044;](install/zsh/zsh.md) | [&#11044;](config/zsh/zsh.md) |
| Vim | [&#11044;](install/vim/vim.md) | [&#11044;](config/vim/vim.md) |
| VS Code |  | [&#11044;](config/vs-code/vs-code.md) |
| pandoc | [&#11044;](install/pandoc/pandoc.md) |  |
| Quarto | [&#11044;](install/quarto/quarto.md) |  |
| Project ID | [&#11044;](install/project-id/project-id.md) | [&#11044;](config/project-id/project-id.md) |
| OpenFOAM | [&#11044;](install/openfoam/openfoam.md) | [&#11044;](config/openfoam/openfoam.md) |
| SU2 | [&#11044;](install/su2/su2.md) | [&#11044;](config/su2/su2.md) |
| PICLas | [&#11044;](install/piclas/piclas.md) | [&#11044;](config/piclas/piclas.md) |
| SPARTA | [&#11044;](install/sparta/sparta.md) | [&#11044;](config/sparta/sparta.md) |

## Configurations

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

#### OpenFOAM-v1706

1.  First we will need to downgrade to the `gcc-7` compiler. Add this to
    `/etc/apt/sources.list`:

    ```sh
    # /etc/apt/sources.list
    deb [arch=amd64] http://archive.ubuntu.com/ubuntu focal main universe
    ```

    Then you can install using

    ```sh
    sudo apt update
    sudo apt install gcc-7 g++-7
    sudo apt install gcc-12 g++-12
    ```

    and update the current compiler 

    ```sh
    sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 7
    sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 7
    sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 11
    sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-11 11
    sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12
    sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-12 12
    sudo update-alternatives --config gcc
    sudo update-alternatives --config g++
    ```

2.  Install OpenFOAM-v1706

    ```sh
    cd $HOME
    mkdir -p OpenFOAM
    cd OpenFOAM


    ```


### 4.2 SU2

## 5. Project-ID Database