---
layout:     post
title:     使用 iwd 作为 NetworkManager 的 WiFi backend
subtitle:   use-iwd-as-nm-wifi-backend
date:       2021-08-20
author:     ALKALiKong
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - NetworkManager
    - iwd
    - WIFI
--- 

## 前言
```iwd``` 是由 Intel 为 Linux 编写的一个无线网络守护程序  
该项目的核心目标是不依赖任何外部库，而是**最大程度地利用 Linux 内核提供的功能来优化资源利用**  
经过我极不严谨的测试，使用 ```iwd``` 的性能比 ```wpa_supplicant``` 要好很多

## 安装
Arch: `# pacman -S iwd`  
Ubuntu: `# apt install iwd`

## 修改 NetworkManager 配置
修改 `/etc/NetworkManager/NetworkManager.conf` ，加入以下内容  

```
[device]
wifi.backend=iwd
```

## 配置 Systemd 服务
屏蔽 `wpa_supplicant` 服务： `# systemctl mask wpa_supplicant`  
启用 `iwd` 服务： `# systemctl enable iwd`  

## 重启
康康有没有效果～
