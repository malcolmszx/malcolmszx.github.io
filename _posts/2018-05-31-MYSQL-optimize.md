---
layout:     post
title: MySQL 性能优化之参数配置
subtitle: Server
date:       2018-05-31
author:     BY Malcolmszx
header-img: img/post-bg-mma-3.jpg
catalog: true
tags:
    - MYSQL
    - 技术
---

## 修改MySQL配置

修改配置文件my.cnf

### MySQL非缓存参数变量介绍及修改

- **thread_concurrency**

thread_concurrency的值对mysql的性能影响很大，尤其在多个cpu(多核)的情况下，设置thread_concurrency值，会导

致mysql不能充分利用系统资源（多cpu多核）。如果设置该值呢？一般情况下，thread_concurrency设为CPU核数的2倍，而不

是cpu个数的两倍。假设一台主机有4个CPU，每个CPU为8核，按照上面的计算规则

，thread_concurrencythread_concurrency的值为：4*8*2=64

查看系统当前thread_concurrency默认配置命令：show variables like 'thread_concurrency';
