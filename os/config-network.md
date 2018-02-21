---
layout: post
title: Config - Network
category: os
tags: [os, linux, mac, unix]
---



# Config - Network

## Ethernet

> $ sudo vi /etc/network/interfaces

```sh
# DHCP
auto eth0
iface eth0 inet dhcp

# Static
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8
```

> $ sudo /etc/init.d/networking restart

