---
title: "WSLでGUI機能を使いたい"
date: 2022-02-12T03:34:09+09:00
draft: false
---
- [動作環境](#動作環境)
- [Windows11とWindows10の違い](#windows11とwindows10の違い)
- [Windows10でのGUI導入手順](#windows10でのgui導入手順)
- [RvizやGazeboが動かない!](#rvizやgazeboが動かない)

# 動作環境
* Windows10
* WSL2 Ubuntu20.04 LTS
  

# Windows11とWindows10の違い
Windows11ではWSLgが提供されており、手間なくGUI機能が使用できる。

参考

https://docs.microsoft.com/ja-jp/windows/wsl/tutorials/gui-apps


# Windows10でのGUI導入手順
1. VcXsrvをWindowsにインストールする
   
    https://sourceforge.net/projects/vcxsrv/
	
    Xlaunchを起動できるようになったら完了
	
    起動時に Disable Access Controlのチェックをつけること

2. WSLのdisplay設定を行う

	.bashrcに以下を追記
    ```
	export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0
    ```

3. xsessionの追記
   ```
	echo xfce4-session > ~/.xsession
    ```
4. 動作確認
   WSLにx11-appsをインストールする
   ```
    sudo apt install x11-apps
	xeyes
    ```

    目玉が動くアプリケーションが起動すればOK

5. もしこれで動かなかったら、ファイヤーウォールの設定を変える
   
    ```6000+ディスプレイ番号```のポートを解放しておく(例：0番目のディスプレイを使う場合6000を解放)

# RvizやGazeboが動かない!
このままRvizやGazeboを動かしたかったが、libGLのエラーに阻まれた

rviz
```
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Segmentation fault
```

gazebo
```
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
```

どうやらXlaunchの起動オプションに```-nowgl```が必要らしい

{{< figure src="/images/wslros/nowgl.png" width="50%">}}

参考

* https://qiita.com/rkoyama1623/items/de467c6b954a6df638c8

* https://demura.net/education/lecture/15304.html

無事起動できた

rviz

{{< figure src="/images/wslros/rviz.png" width="50%">}}

gazebo

{{< figure src="/images/wslros/gazebo.png" width="50%">}}