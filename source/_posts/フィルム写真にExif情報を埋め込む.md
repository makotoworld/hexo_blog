---
title: フィルム写真にExif情報を埋め込む
date: 2020-04-03 22:24:16
tags:
    - photo
    - exiftool
---

# フィルム写真
デジタルカメラがまだ復旧していなかった写真が膨大にあり、macOSのリニューアルで使えなくなったScanSnapを買い換えた当時に整理し始めた。（ほとんど嫁がやってるけれど…有難う御座います）

スキャンして、Googleフォトにあげようと思ったら、このままじゃ撮影日時が実際の日時とすごくズレている。。。

20年前の写真なのに。。。

何かいいかなーと思ったら、「exiftool」というものを発見した。

開発した Phil Harvey さんが 開発、リリースしている。

* [ExifTool by Phil Harvey](https://exiftool.org/)

# Install
* macOS ならdmg、brewでもOK
  * https://exiftool.org/ExifTool-11.92.dmg
  * brew

````
> brew install exiftool
````

# 書き換えるためのコマンド
ググって見た情報だと、「-alldates」って書いてあるのがほとんどで試したら変わらず、オリジナルファイルが複製されただけだった。
いろいろ検証してみると、「-FileModifyFile」でいけた。
````
> exiftool -FileModifyDate='2006:05:03 08:00:00' *.jpg
````


# Eixf 情報が書き込まれているかの確認
* previewのインペクタ(⌘+I)で確認できる。

* exiftool 001.jpg でもOK。
````
❯ exiftool さざえ＆まこと結婚式.jpg
ExifTool Version Number         : 11.85
File Name                       : さざえ＆まこと結婚式.jpg
Directory                       : .
File Size                       : 260 kB
File Modification Date/Time     : 2006:05:03 08:00:00+09:00
File Access Date/Time           : 2020:04:03 23:24:26+09:00
File Inode Change Date/Time     : 2020:04:03 23:24:26+09:00
File Permissions                : rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Exif Byte Order                 : Big-endian (Motorola, MM)
Orientation                     : Horizontal (normal)
X Resolution                    : 600
Y Resolution                    : 600
Resolution Unit                 : inches
Modify Date                     : 2006:05:03 08:00:00
Date/Time Original              : 2006:05:03 08:00:00
Create Date                     : 2006:05:03 08:00:00
Color Space                     : sRGB
Exif Image Width                : 2748
Exif Image Height               : 2081
Current IPTC Digest             : d41d8cd98f00b204e9800998ecf8427e
IPTC Digest                     : d41d8cd98f00b204e9800998ecf8427e
Image Width                     : 2748
Image Height                    : 2081
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2748x2081
Megapixels                      : 5.7
````

# 寄付しようと思ったら
* [ExifTool by Phil Harvey](https://exiftool.org/#donate)

素晴らしいツールだし、今後も開発を続けてほしいという気持ちを込めて、PayPal経由で寄付しようと思ったら、日本からだと受け付けてないみたい…。残念。

# 参考にしたURL（ありがとうございます）
* [ExifTool by Phil Harvey](https://exiftool.org/)
* [写真ファイルの撮影日時を変更する – sgryjp\.log\.old](http://sgry.jp/blog/2017/01/01/4002/#mac-photo)
* [Mac で Exif を編集したり削除したりできる「ExifTool」 \| 使える機材 Blog！](https://panproduct.com/blog/?p=23709)
* [メモ：exiftoolで画像のEXIF情報を変更する \- Qiita](https://qiita.com/nekogesaku/items/bc4df484b1de2ac6cda0)

# おすすめアイテム
{% AmazonJpLink2 "B07HHZJKS3" "makotoworld0a-22" "富士通 PFU ドキュメントスキャナー ScanSnap iX1500 (両面読取/ADF/4.3インチタッチパネル/Wi-Fi対応)" %}
