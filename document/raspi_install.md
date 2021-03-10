# Raspberry Pi の初期設定

## 準備するもの
- [Raspberry Pi Zero W](https://www.raspberrypi.org/products/raspberry-pi-zero-w/)
- [microSD カード (16GB)](https://www.amazon.co.jp/HIDISC-microSDHC%E3%83%A1%E3%83%A2%E3%83%AA%E3%82%AB%E3%83%BC%E3%83%89-CLASS10-UHS-I-HDMCSDH16GCL10UIJPWO/dp/B01MR5O56L/)
- [microSD カード の読み込み機器](https://www.amazon.co.jp/Transcend-Super-%E3%82%AB%E3%83%BC%E3%83%89%E3%83%AA%E3%83%BC%E3%83%80%E3%83%BC-microSDXC-TS-RDF5K/dp/B009D79VH4)

## Raspberry Pi OS のインストール

Raspberry Pi Imager を利用してインストールする

- [Raspberry Pi Imager](https://www.raspberrypi.org/software/) 

![スクリーンショット 2021-03-10 22 27 53](https://user-images.githubusercontent.com/31144411/110636667-df646e80-81ef-11eb-9406-1d8c58d50ed6.png)


## 初期のネットワーク設定（SSH出来るまで）

microSD を Mac で `/Volumes/boot` に Mount する。


SSH を有効化する
- `touch /Volumes/boot/ssh`

WIFI の設定をする

- `vi /Volumes/boot/wpa_supplicant.conf`
  ```
  ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
  update_config=1
  country=JP

  network={
        ssid="<WIFI の SSID>"
        psk="<WIFI の パスワード>"
  }
  ```

### Raspberry Pi に SSH で接続する

Rasberry Pi zero Wの初期パスワード : raspberry
```
% ssh pi@raspberrypi.local
pi@raspberrypi.local's password: <パスワード入力>
```

初期パスワードを変更する
```
pi@raspberrypi:~ $ passwd
```