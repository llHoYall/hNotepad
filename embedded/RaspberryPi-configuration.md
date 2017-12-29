---
layout: poat
title: [Raspberry-Pi] configuration
category: python
tags: python
---

&nbsp;

# [Raspberry-Pi] configuration


### Installation

#### 1. Download Image

<https://www.raspberrypi.org/downloads>

  - Raspbian
  - Ubuntu Mate

#### 2. Install Image

##### 2.1. Windows

<https://sourceforge.net/projects/win32diskimager>

##### 2.2. MAC

microSD mount 확인.

> $ diskutil list

microSD에 OS 설치.

> $ sudo diskutil unmountDisk /dev/disk#
> $ sudo dd bs=1m if=xxx.img of=/dev/disk#

----

### Configuration

Raspberry Pi를 설정하는 방법이다.

기본 계정은 다음과 같다.

> ID: pi
> PW: raspbeery

##### root 계정 활성화.

> **$ sudo passwd root**

##### 라즈베리파이 설정.

> **$ sudo raspi-config**

버전마다 메뉴의 위치가 다르다. 다음의 설정을 해준다.

- Expand Filesystem
- Change User Password
- SSH
- Keyboard

##### 사용자 계정 추가.

> \# 기본 사용자 계정 삭제.
> **$ sudo userdel -r pi**
> \# -r : 홈 디렉토리까지 삭제.
>
> **$ sudo useradd -m -d /home/\<*account*\> \<*account*\>**
> \# -m : 사용자 홈 디렉토리를 생성하고 쉘초기화 파일을 복사한다.
> \# -d : 사용자 홈 디렉토리의 절대경로.
>
> **$ sudo passwd \<*account*\>**

##### 삼바 설정.

> **$ sudo apt install samba**
> **$ sudo smbpasswd -a \<*account*\>**
> **$ sudo vi /etc/samba/smb.conf**

```sh
[account]
comment='rpi samba'
path=/home/account/work
valid user=account
writable=yes
browseable=yes
```

> **$ sudo service smbd restart**
> **$ sudo update-rc.d samba defaults**

#### 인터넷 설정

##### 1. ethernet

>  **$ sudo vi /etc/network/interfaces**

```sh
iface lo inet loopback
iface eth0 inet dhcp
```

>  **$ sudo /etc/init.d/networking restart**

##### 2. Wi-Fi

> **$ sudo vi /etc/network/interfaces**

```sh
iface wlan0 inet dhcp
```

> **$ sudo vi /etc/wpa_supplicant/wpa_supplicant.conf**

```sh
network={
	ssid="SSID"
	psk="PASSWORD"
}
```

> **$ sudo ifdown wlan0**
> **$ sudo ifup wlan0**

----

### 프로그램 설치

> **$ sudo apt-get update**
> **$ sudo apt-get upgrade -y**
> **$ sudo apt-get dist-upgrade -y**
> **$ sudo rpi-update**