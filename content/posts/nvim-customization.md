---
title: "Neovim Customization"
date: 2022-07-03T08:48:38+05:30
draft: true
tags: ["neovim", "vi", "ricing", "productivity"]

author: "Me"
showToc: true
TocOpen: true
draft: false
hidemeta: false
comments: false
description: ""
canonicalURL: "https://iamb4uc.xyz/to/page"
disableShare: false
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: img/neovim.png
    alt: 'This is a post image'
    caption: 'A Basic Minimal Neovim Configuration'
---

## Why use vim over other text editors and IDEs?
For me, I've always loved minimalism and performance over ease of use and other flashy bloat no one really uses and cares about. This why I personally use Terminal-based text editors. Preferably VIM or NeoVIM. Tho I currently, am running NeoVIM, but both of them are basically the same. NeoVIM is a little bit more extensible than VIM and easy to manage imo. But enough talking, lets start configuring our VIM/NVIM to make it more like an actual developing environment.  

**IMPORTANT:** Since I mainly use Neovim, some of the stuff written in this blog might not work for vim users, for them just avoid the once that are not compatible, if I find any alternatives to those plugins and setting, I will update the blogs with the details.

### Step 1: Setting up the config files and directory for vim and neovim
Follow the commands given below to make all the necessary files and directories for neovim

```bash
cd
mkdir -p ~/.config/nvim
touch ~/.config/nvim/init.vim
```
The **init.vim** file is the config file that we will edit in this post to make our base neovim to look and act like an actual IDE.

### Step 2: Editing the init.vim file
To edit this **init.vim** open the file with the text editor of your choice and paste the following text

```vim
:set number
:set relativenumber
:set autoindent
:set expandtab
:set tabstop = 4
:set shiftwidth = 4
:set smarttab
:set softtabstop = 4
```

These parameters set basic functionality for vim such as number lines, auto indentation, amd smart tabs. By default vim doesnt support mouse and its kinda normal to not use mouse since everything in vim can be done using the keyboard but if you are a soy and want to use mouse type this this too
```vim
:set mouse = a
```

For now we have done all the basic settings.

### Step 3: Adding a Plug-In Manager
For this setup we will use Vim-Plug to manage our plugins.  
1. Install Curl  
    **Debian-based**
    ```
    sudo apt install curl
    ```
    
    **Gentoo**
    ```
    sudo emerge curl
    ```
    
    **RHEL, Fedora and other Red Hat Derivaties**
    ```
    sudo yum install curl
    ```
    
    **Arch-based**
    ```
    sudo pacman -S curl
    ```
    
    **Void**
    ```
    sudo xbps-install curl
    ```

2. Create the installation directories, download, and install Vim-Plug. 
```
sudo curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

### Step 4: Installing Plug-ins
In your init.vim file, add these lines at the bottom of what we previously wrote.  
```vim
call plug#begin()



call plug#end()
```

We will be able to add plugins in between the two commands.  

Now we will add our first plug-in  

Find the desireable plug-ins from [VIM Awesome](https://vimawesome.com/) this is one of the best places to find vim and neovim plugins.  
For this tutorial we will add couple of plug-ins to make our neovim look good and work like an ide.  
```vim
Plug 'tpope/vim-fugitive'                   " Git integration in to nvim
Plug 'Yggdroot/indentLine'                  " Line Indentations
Plug 'farmergreg/vim-lastplace'             " Continue from where you left last time
Plug 'raimondi/delimitmate'                 " Provides insert mode auto-completion for special-characters
Plug 'tpope/vim-markdown'                   " Markdown runtime files
Plug 'tpope/vim-surround'                   " Change paranthesis and quotes into other forms quickly
Plug 'scrooloose/nerdtree'                  " File navigator
Plug 'vim-scripts/indentpython.vim'         " Indentation script for python
Plug 'alvan/vim-closetag'                   " Makes a close tag for html quickly
Plug 'luochen1990/rainbow'                  " Provides different colors to different paranthesis
Plug 'airblade/vim-gitgutter'               " Shows git diffs in the sign columns
Plug 'lilydjwg/colorizer'                   " Provides color for the #rrggbb or #rgb color format in files
Plug 'vim-airline/vim-airline'              " Powerline Theme / Status line
Plug 'vim-airline/vim-airline-themes'       " Themes for vim-airline
Plug 'rafi/awesome-vim-colorschemes'        " Change colorschemes on the fly for vim and nvim
Plug 'ryanoasis/vim-devicons'               " Icons
Plug 'SirVer/ultisnips'                     " Code completion using snippets from vim-snippets and custom snippets
Plug 'honza/vim-snippets'                   " Provides snippets for ultisnips
```

### (OPTIONAL)Adding Code-suggestions
This section is a bit tidious and is only available for neovim users so if you use vim this section is irrelevnet to you.  
Add this plug-in in your init.vim file.
```vim
Plug 'neoclide/coc.nvim'                    " Code suggestions and completion
```

Now this plugin wont run without npm in your machine so follow these steps to make it work.  

