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

#### max_connections

max_connections参数指的是MySql的最大连接数，如果服务器的并发连接请求量比较大，建议调高此值，以增加并行连接数量，当然这建立在机器能支撑的情况下，因为如果连接数越多，介于MySql会为每个连接提供连接缓冲区，就会开销越多的内存，所以要适当调整该值，不能盲目提高设值。可以过'conn%'通配符查看当前状态的连接数量，以定夺该值的大小。注意：MySQL服务器允许的最大连接数16384;
查看系统当前最大连接数：show variables like 'max_connections';

#### back_log

如果MySql的连接数据达到max_connections时，新来的请求将会被存在堆栈中，以等待某一连接释放资源，该堆栈的数量即back_log，如果等待连接的数量超过back_log，将不被授予连接资源。将会报：unauthenticated user xxx.xxx.xxx.xxx  NULL  Connect  NULL  login  NULL ，等待连接进程时，back_log值不能超过TCP/IP连接的侦听队列的大小，若超过则无效。

查看当前系统的TCP/IP连接的侦听队列的大小命令：cat /proc/sys/net/ipv4/tcp_max_syn_backlog目前系统为1024。对于Linux系统推荐设置为小于512的整数，修改系统内核参数。http://www.51testing.com/html/64/n-810764.html

查看mysql 当前系统默认back_log值，命令：show variables like 'back_log';