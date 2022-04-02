---
title: "Ubuntu_setup"
date: 2022-04-03T00:55:01+09:00
draft: false
---

# 動作環境
* Ubuntu18.04 LTS, 20.04 LTS向け
  

# ubuntuをインストールしたらやることリスト

* update upgrade
   
    ```
	sudo apt update
    sudo apt upgrade
    ```

* proxy環境下の場合proxyを設定する
    ~/.bashrcに以下を追記
    ```
    export http_proxy="http://****"
    export https_proxy=$http_proxy
    export ftp_proxy=$http_proxy
    ```

    aptの方もproxyを設定する /etc/apt/apt.confを設定
    ```
    Acquire::http::proxy "http://****";
    Acquire::https::proxy "https://****";
    ```

* aptでいろいろインストールする(お好み)
    ```
    sudo apt install git vim net-tools meld vlc -y
    ```

* git config

    ```
    git config --global user.name "name"
    git config --global user.email name@example.com
    ```

* 日本語入力をできるようにする
    ```
    sudo apt install ibus-mozc 
    ibus restart 
    gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'jp'), ('ibus', 'mozc-jp')]"
    ```

* 日本語のフォルダ名を英語にする(日本語版限定)

    ```
	LANG=C xdg-user-dirs-gtk-update
    ```

* capslockをctrlにする
    
    ```
	gsettings set org.gnome.desktop.input-sources xkb-options "['ctrl:nocaps']"
    ```

* gitブランチを端末に表示する

    bashrcに追記
    ```
    export PS1='\[\033[01;32m\]\u@\h\[\033[01;33m\] \w \[\033[01;31m\]$(__git_ps1 "(%s)") \n\[\033[01;34m\]\$\[\033[00m\] '
    ```

* その他よく使うソフトウェアをインストールする

    chrome, vscode, simplescreenrecorderなど
