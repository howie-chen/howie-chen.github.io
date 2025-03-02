---
title: 搭建 Mac 本地开发环境
date: 2025-03-02
---

## 重新安装 macOS

https://support.apple.com/zh-cn/102342

## 初始化开发环境

1. 配置好网络代理。

2. 需要时，在终端使用代理：
  ```
  export http_proxy="http://localhost:6152" && export https_proxy="http://localhost:6152"
  ```

3. Homebrew

4. nvm
  - auto switch node version when change pwd

5. pyenv  (install via homebrew, add 3 lines to zshrc)

6. rvm

7. JDK 8

8. Oh-My-Zsh with Spaceship theme

9. Set up other tools
  - [配置 OpenFortiVPN](../set-up-openfortivpn)
  - [配置 Oh My Zsh 和 Spaceship theme](../set-up-oh-my-zsh-and-spaceship-theme)
  - [配置 SSH 会话时长](../keep-alive-for-ssh-sessions)

10. 安装命令行小工具
  ```
  brew install bat exa
  ```

