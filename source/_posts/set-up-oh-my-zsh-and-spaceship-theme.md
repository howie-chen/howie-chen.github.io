---
title: 配置 Oh My Zsh 和 Spaceship theme
date: 2025-03-02
---

## Pre-requisite

1. Install zsh (v5.2 or recent).
    - By default, it’s already included in macOS 10.15 Catalina as default shell.
2. Install Oh My Zsh.
    
    ```bash
    sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    ```
    
3. Install Powerline Fonts and switch font to Fira Mono for Powerline.
    
    ```bash
    git clone https://github.com/powerline/fonts.git --depth=1
    cd fonts
    ./install.sh
    ```
    

## Instructions

1. Install Spaceship ZSH via Oh My Zsh.
    
    ```bash
    git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt"
    ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
    # Set ZSH_THEME="spaceship" in your .zshrc.
    ```
    
2. Open a new tab in your Terminal app to take effect.

## Plugins

You must open a new tab or restart your terminal to take effect.

### Zsh Syntax Highlighting

1. Clone the repository.
    
    ```bash
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```
    
2. Activate the plugin in ~/.zshrc:
    
    ```bash
    plugins=(... zsh-syntax-highlighting)
    ```
    

### Auto Jump

1. Install via brew.
    
    ```bash
    brew install autojump
    ```
    
2. Add the following line to ~/.zshrc:
    
    ```bash
    [ -f /usr/local/etc/profile.d/autojump.sh ] && . /usr/local/etc/profile.d/autojump.sh
    ```
    

### git-open

1. Clone the repository.
    
    ```bash
    git clone https://github.com/paulirish/git-open.git $ZSH_CUSTOM/plugins/git-open
    ```
    
2. Activate the plugin in ~/.zshrc:
    
    ```bash
    plugins=(... git-open)
    ```