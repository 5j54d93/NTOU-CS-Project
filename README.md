# NTOU CS Project

[![CodeQL](https://github.com/5j54d93/NTOU-CS-Project/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/5j54d93/NTOU-CS-Project/actions/workflows/codeql-analysis.yml)
![GitHub](https://img.shields.io/github/license/5j54d93/NTOU-CS-Project)
![GitHub Repo stars](https://img.shields.io/github/stars/5j54d93/NTOU-CS-Project)
![GitHub repo size](https://img.shields.io/github/repo-size/5j54d93/NTOU-CS-Project)

Using Raspberry Pi 3 Model B+ to help us auto watering plants, and if there are birds aproaching, buzzer will noise to scare them away！We also have a dashboard（web）to view all related data which could auto switching between Day theme and Nithgt theme！And you could also remote control Raspberry Pi to watering or noising by clicking the button on website if you want！

<img src="https://github.com/5j54d93/NTOU-CS-Project/blob/main/.github/assets/Product.png" width='100%' height='100%'/>

## Overview

1. [Wiring to Raspberry Pi](https://github.com/5j54d93/NTOU-CS-Project#ntou-cs-projectwiring-to-raspberry-pi)
   - [Check the I2C devices](https://github.com/5j54d93/NTOU-CS-Project#check-the-i2c-devices)
   - [Check the SPI devices](https://github.com/5j54d93/NTOU-CS-Project#check-the-spi-devices)
2. [Install Libraries on Raspberry Pi](https://github.com/5j54d93/NTOU-CS-Project#ntou-cs-projectinstall-libraries-on-raspberry-pi)
3. [Download this Repository on Raspberry Pi](https://github.com/5j54d93/NTOU-CS-Project#ntou-cs-projectdownload-this-repository-on-raspberry-pi)
5. [Run Web Server on Raspberry Pi](https://github.com/5j54d93/NTOU-CS-Project#ntou-cs-projectrun-web-server-on-raspberry-pi)
6. [Open the Website](https://github.com/5j54d93/NTOU-CS-Project#ntou-cs-projectopen-the-website)
   - [Screenshot with Day theme and Nithgt theme（Automatic switching）](https://github.com/5j54d93/NTOU-CS-Project#screenshot-with-day-theme-and-nithgt-themeautomatic-switching)
- [Block Diagram](https://github.com/5j54d93/NTOU-CS-Project#ntou-cs-projectblock-diagram)
- [License](https://github.com/5j54d93/NTOU-CS-Project#ntou-cs-projectlicense-ntou-cs-2021-ricky-chuang)

## Wiring to Raspberry Pi

- **［I2C］Light**：APDS9960
- **［I2C］Air Quality**：SGP30
- **［I2C］Temperature & Humidity**：SHT31-D
- **［SPI］Acceleration**：ADXL203EB
- **［GPIO］Watering**：Bump
- **［GPIO］Noise**：Buzzer

### Check the I2C devices：

|SGP30：`0x58`|APDS9960：`0x39`|SHT31-D：`0x44`|
|:-:|:-:|:-:|

```shell
pi@raspberrypi:~ $ sudo i2cdetect -y 1
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- --
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
30: -- -- -- -- -- -- -- -- -- 39 -- -- -- -- -- --
40: -- -- -- -- 44 -- -- -- -- -- -- -- -- -- -- --
50: -- -- -- -- -- -- -- -- 58 -- -- -- -- -- -- --
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
70: -- -- -- -- -- -- -- --
```

### Check the SPI devices：

|**Raspberry Pi**|→|**MCP3008**|→|**ADXL203EB**|
|:-:|:-:|:-:|:-:|:-:|

```shell
pi@raspberrypi:~ $ ls -l /dev/spidev*
crw-rw---- 1 root spi 153, 0 Aug 28 13:17 /dev/spidev0.0
crw-rw---- 1 root spi 153, 1 Aug 28 13:17 /dev/spidev0.1
```

## Install Libraries on Raspberry Pi

```shell
sudo pip3 install -r requirements.txt
```

## Download this Repository on Raspberry Pi

```shell
git clone https://github.com/5j54d93/NTOU-CS-Project
```

## Run Web Server on Raspberry Pi

```shell
cd NTOU-CS-Project
sudo python3 Demeter.py
```

## Open the Website

You could open it on computer, iPhone, iPad ......, as long as your device has a browser.  
_Make sure your device and Raspberry Pi are connect to the same WiFi._

- **URL：`http://[your ip]`**
- use `ifconfig` to check your ip
- replace `[your ip]` to something like `192.xxx.x.xx` or `192.xxx.x.xxx`

### Screenshot with Day theme and Nithgt theme（Automatic switching）

<img src="https://github.com/5j54d93/NTOU-CS-Project/blob/main/.github/assets/Screenshot.png" width='100%' height='100%'/>

## Block Diagram

<img src="https://github.com/5j54d93/NTOU-CS-Project/blob/main/.github/assets/Block%20Diagram.png" width='100%' height='100%'/>

## License：MIT

This package is [MIT licensed](https://github.com/5j54d93/NTOU-CS-Project/blob/main/LICENSE).
