+++
title = "Mac Config"
date = 2019-12-02T00:00:00-05:00
draft = false
+++

This is a demo.

<!--more-->


## Install {#install}

```nil
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew cask install google-chrome
brew cask install google-backup-and-sync
brew cask install iterm2
brew cask install sogouinput
brew cask install karabiner-elements
brew cask install bettertouchtool
brew cask install contexts
brew cask install clipy
brew cask install moom
brew cask install atext
brew cask install captin
brew cask install 1password
brew cask install virtualbox
brew cask install vagrant
brew cask install emacs
brew cask install vlc
brew tap homebrew/cask-fonts
brew cask install font-source-code-pro
```


## System preferences {#system-preferences}


### General {#general}

-   Appearance: Dark
-   Show scroll bars: When scrolling
-   Recent items: None


### Dock {#dock}

-   Size: Small
-   Position on screen: Left
-   Unchech "Show recent applications in Dock"


### Mouse {#mouse}

-   Uncheck "Scroll direction: Natural"


### Sound {#sound}

-   Check "Show volume in menu bar"


### Login Items {#login-items}

-   Users & Groups -> Login Items
    -   Bettertouchtool
    -   Clipy
    -   Karabiner
    -   Contexts
    -   Moom
    -   aText
    -   Captin
    -   Hazeover
    -   1password


### Energy Saver {#energy-saver}

-   Computer sleep: 3h
-   Display sleep: 3h


### Notifications {#notifications}

-   Turn off all


## Finder {#finder}

-   Preferences
    -   General -> New Finer windows show: Destop
    -   General -> Check "Open folders in tabs instead of new windows"
    -   Sidebar -> Favorites: AirDrop, Applications, Desktop, Documents, Downloads, weiz, mac-mini
    -   Sidebar -> Uncheck "Recent Tags"
    -   Advanced -> Check "Show all filename extensions"
-   View
    -   Show status bar
    -   Show path bar
-   Column view


## Contexts {#contexts}

-   Load license
-   Sidebar -> Show Sidebar on -> No display
-   Search -> uncheck "Search with"
-   Command-Tab
    -   Select Option-Tab, uncheck others
    -   Activate switcher with: Option-Tab
    -   Move up list with: Option-Shift-Tab
    -   Show windows from: Visible Spaces
    -   Show windows of: All apps
    -   Minimized windows: Do not show
    -   Hidden windows: Do not show
    -   Apps without windows: Do not show
    -   Show: Neither
-   Load license


## Hazeover {#hazeover}

-   Load license
-   Dim: 50%


## Clipy {#clipy}

-   General
    -   Max clipboard history size: 10
-   Menu
    -   Number of items place inline: 10
    -   Number of items place inside a folder: 10


## Captin {#captin}

-   Preferences
    -   General -> check "Launch Captin at login"
    -   General -> uncheck "Show preferences on launch"
    -   Icon -> uncheck "Show dock icon"


## aText {#atext}

-   Preferences -> General -> uncheck "Show aText icon in Dock"
-   Delete all pre-abbreviation, leave only "Default"
-   Load license


## Moom {#moom}

-   General
    -   Run as "menu bar" application
    -   check "Launch Captin at login"
    -   uncheck "Show preferences on launch"
-   Keyboard
    -   Trigger keyboard control with hot key: "option+escape"
    -   Show logo
    -   Show cheat sheet
-   Load license


## Sogou input {#sogou-input}

-   Install

    ```nil
    open xxx.app
    ```
-   Keyboard -> Shortcuts -> Input Sources -> Check "Select previous input source"
-   偏好设置
    -   状态栏提示: uncheck all
    -   外观: 简约黑
    -   统计: uncheck all


## VLC {#vlc}

-   Preferences -> Interface -> Interface style dark
-   Preferences -> Audio -> Keep audio level between sessions
-   Preferences -> Show All -> Interface
    -   Main interfaces -> macosx -> uncheck "Keep Recent Items"
    -   Hotkey settings -> Mouse wheel vertical axis control: Position control reversed


## Iterm2 {#iterm2}

-   Appearance
    -   Theme: Minimal
    -   Tab bar location: Top
    -   Status bar location: Bottom
-   Profiles
    -   Text -> Font: Source Code Pro, Regular, 13
    -   Terminal -> Notifications: check "Silence bell" and "Flash visual bell"
    -   Session -> check "Status bar enabled"
    -   Session -> Configure Status Bar: CPU, Memory, Network, Battery (auto rainbow)
    -   Keys -> Left Option Key: Esc+
    -   Keys -> Right Option Key: Esc+


## Spacemacs {#spacemacs}

-   Install

    ```nil
    git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
    ```
-   Install aspell for spell checking

    ```nil
    brew install aspell
    ```
-   evil-operators
    -   s,d,x,c,y
-   evil-textobj (<https://github.com/laishulu/evil-textobj-syntax>)
    -   argument
    -   word
    -   sub-word
    -   ()
    -   {}
    -   []
    -   <>
    -   ""
    -   ''
    -   \`\`
-   evil-easymotion (<https://github.com/PythonNut/evil-easymotion>)


## Bettertouchtool {#bettertouchtool}

-   Load license


## Google Backup and Sync {#google-backup-and-sync}

-   Disable all computer backup


## Chrome {#chrome}

-   Default browser
-   Downloads -> Location: Desktop
-   Autofill -> Disable "Passwords, Payment methods, Address and more"
-   Search engine
    -   g: google
    -   d: youdao
-   Privacy and security -> Site Settings -> Notifications -> Block
-   Extensions
    -   Adblock Plus
    -   Unblock Youku
    -   1password
    -   有道词典Chrome划词插件
        -   指词即译模式（按下Ctrl键指词）
        -   仅对英文划译
        -   点击发音
    -   Hyperlink Text Selector
    -   Surfingkeys


## Vagrant {#vagrant}

-   Init

    ```nil
    vagrant init ubuntu/bionic64
    mkdir workspace
    ```
-   Vagrantfile

    ```nil
    config.vm.synced_folder "./workspace", "/home/vagrant/workspace"
    config.vm.network "forwarded_port", guest: 8000, host: 8000, host_ip: "127.0.0.1"
    config.vm.network "forwarded_port", guest: 8080, host: 8080, host_ip: "127.0.0.1"
    config.vm.network "forwarded_port", guest: 1313, host: 1313, host_ip: "127.0.0.1"
    config.ssh.forward_agent = true

    sudo snap install tree
    ```
-   SSH agent on host

    ```nil
    ssh-keygen # And add public key to SSH

    eval "$(ssh-agent -s)"

    cat <<EOF > ~/.ssh/config
    Host *
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/id_rsa
    EOF

    ssh-add -K ~/.ssh/id_rsa
    ```
-   Trinity

    ```nil
    sudo apt install zsh
    cd workspace
    git clone git@github.com:vitmy0000/trinity.git
    # vim-plug
    curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
    # zplug
    curl -sL --proto-redir -all,https https://raw.githubusercontent.com/zplug/installer/master/installer.zsh| zsh

    ln -s workspace/trinity/tmux.conf ~/.tmux.conf
    ln -s workspace/trinity/gitconfig ~/.gitconfig
    ln -s workspace/trinity/vimrc ~/.vimrc
    ln -s workspace/trinity/zshrc ~/.zshrc

    echo 'export SHELL=$(which zsh)' >> ~/.bashrc
    echo '[ -z "$ZSH_VERSION" ] && exec "$SHELL" -l' >> ~/.bashrc

    tmux new -s Main
    ```
-   Hugo

    ```nil
    sudo snap install hugo
    hugo version

    mkdir hugo
    cd hugo
    hugo new site quickstart
    cd quickstart
    git init
    git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
    echo 'theme = "ananke"' >> config.toml
    hugo new posts/my-first-post.md
    hugo server --bind "0.0.0.0"

    http://localhost:1313/
    ```
-   Oat++

    ```nil
    sudo snap install cmake --classic
    sudo apt install build-essential

    # oat++
    mkdir oatpp
    cd oatpp
    git clone https://github.com/oatpp/oatpp.git
    cd oatpp/
    mkdir build && cd build
    cmake ..
    make install

    # oat app
    git clone https://github.com/oatpp/oatpp-starter.git
    cd oatapp-starter
    mkdir build && cd build
    cmake ..
    make
    ./my-project-test
    ./my-project-exe  # - run application.
    ```
-   Vue

    ```nil
    sudo apt install npm
    sudo npm i -g @vue/cli
    vue --version

    mkdir vue
    cd vue
    vue create vue-demo
    cd vue-demo
    npm run serve

    vue ui -H 0.0.0.0 --headless
    ```
-   Dr racket
-   Haskell


## Issues {#issues}

-   VLC window size
-   Surfingkeys not working on Chrome reserved pages
-   Night shift fullscreen