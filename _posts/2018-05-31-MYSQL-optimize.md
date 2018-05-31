---
layout:     post
title: MySQL 性能优化之参数配置
subtitle: 修改 my.cnf
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

#### thread_concurrency

合理地设置thread_concurrency的值，对mysql的性能影响很大，尤其在多个cpu(多核)的情况下，该值设置不当会直接导致mysql不能充分利用系统资源（多cpu多核），一般情况下，thread_concurrentcy的值，设置为cpu核数的两倍,查看系统当前thread_concurrency默认配置命令：show variables like 'thread_concurrency';

