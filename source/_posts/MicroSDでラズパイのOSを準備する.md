---
title: MicroSDでラズパイのOSを準備する
date: 2020-03-30 09:37:29
tags:
        - [raspberrypi]
---

毎回ググって調べたりしているので、ここで自分の環境に合わせた手順を書いてみた。
* macOS
* 物理キーボード及びマウス、有線LANケーブルなし
* Wi-Fiあり、SDカード変換アダプターあり
* GUI(VNC)で操作したい

# RaspberryPiのOSイメージを用意する
* [Download Raspbian for Raspberry Pi](https://www.raspberrypi.org/downloads/raspbian/)
![](https://i.imgur.com/JWn2jnT.png)

# microSDを初期化する
* [SD Memory Card Formatter \- SD Association](https://www.sdcard.org/downloads/formatter/)
![](https://i.imgur.com/U3wfO9L.png)
![](https://i.imgur.com/4iGyQWD.png)

# misroSDにOSイメージを書き出す
* [balenaEtcher \- Flash OS images to SD cards & USB drives](https://www.balena.io/etcher/)
![](https://i.imgur.com/ddQdWL9.png)
* ソフトを開いた時の画面。
![](https://i.imgur.com/kaZZQXR.png)
* 「＋」のところ、ダウンロードしたOSイメージ（ZIPファイル）を選択。
* 準備ができたら、「Flash!」をクリックすると、microSDに書き出しが始まる。
* おおよそ20分くらいかかる。

# SSHの設定を行う
* ssh接続するためには、空の ssh ファイルを設置する。
* microSDをSDカード変換アダプターに入れて、macOS に読み込ませる。

```
cd /Volumes/boot
touch ssh
```

# Wi-Fiの設定を行う
* Wi-Fi接続するためには、wpa_supplicant.conf を作成する。
* 作っておくと自動的につながるようになる。

```
vi wpa_supplicant.conf
wpa_supplicant.conf
country=JP
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
network={
    ssid="abc"
    psk=bac3cdf26d42c3a61fb858ef0295a0166e94f84dbabc1088bfa090cef3cb1dcb
}
```

# SSH接続し、OSのアップデート
* raspberry pi を起動し、macOS のターミナルからSSH接続する

```
pi@raspberrypi:~ $ ssh pi@raspberrypi.local
```

* password は初期で、「raspberry」
* `passwd` で変更できる。

```
pi@raspberrypi:~ $ passwd
pi 用にパスワードを変更中
Current password:
新しいパスワード:
新しいパスワードを再入力してください:
passwd: パスワードは正しく更新されました
```

* ライブラリのアップデートを行う。

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

# VNC接続の設定を行う

```
sudo apt-get install tightvncserver
sudo apt-get install realvnc-vnc-server
```

# 参考URL
  * [Raspberry Pi へのリモート接続 \- Qiita](https://qiita.com/b-wind/items/d33f759ace01658bb09e#vnc%E3%82%92%E6%9C%89%E5%8A%B9%E3%81%AB%E3%81%99%E3%82%8B)

# おすすめアイテム
{% AmazonJpLink2 "B081YD3VL5" "makotoworld0a-22" "【国内正規代理店品】Raspberry Pi4 ModelB 4GB ラズベリーパイ4 技適対応品" %}
