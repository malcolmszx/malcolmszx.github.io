---
layout:     post
title:  Linux 常用命令总结
subtitle:  模块化
date:       2018-06-01
author:     BY Malcolmszx@gmail.com
header-img: img/post-bg-miui6.jpg
catalog: true
tags:
    - 终端
    - linux
---

# Linux 常用命令

## 系統

- uname -a 查看内核/操作系统/cpu信息

- head -n l /etc/issue 查看操作系统版本

- cat/proc/cpuinfo 查看cpu信息

- hostname 查看计算机名

- lspci -tv 列出所有PCI设备

- lsusb -tv 列出所有USB设备

- lsmod 列出加载的内核模块

- env 查看环境变量

## 资源

- free -m 查看内存使用量和交换区使用量

- df -h 查看各分区使用情况

- du -sh （目录名） 查看指定目录的大小

- grep MenTotal /proc/meminfo 查看内存总量

- grep MenTotal /proc/meminfo 查看空闲内存量

- uptime 查看系统运行时间、用户数、负载

- cat/proc/loadavg 查看系统平均负载


