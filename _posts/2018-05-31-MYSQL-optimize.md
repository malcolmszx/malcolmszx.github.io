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

### MySQL缓存变量介绍及修改

数据库属于IO密集型的应用程序，职责是数据的管理及存储。从内存中读取一个数据库的时间是微秒级别，而从一块普通硬盘上读取一个IO是在毫秒级别，二者相差3个数量级。

因此，要优化数据库，首先第一步需要优化的就是IO，尽可能将磁盘IO转化为内存IO。

从MySQL数据库IO相关参数(缓存参数)的角度可以通过哪些参数进行IO优化？

#### innodb_buffer_pool_size 

innodb_buffer_pool_size:主要针对InnoDB表性能影响最大的一个参数。功能与Key_buffer_size一样。InnoDB占用的内存，除innodb_buffer_pool_size用于存储页面缓存数据外，另外正常情况下还有大约8%开销，主要用在每个缓存页帧的描述、adaptive hash等数据结构，如果不是安全关闭，启动时还要恢复的话，还要另开大约12%的内存用于恢复，两者相加就有差不多21%的开销。
 
假设：12G的innodb_buffer_pool_size，最多的时候InnoDB就可能占用到14.5G的内存。若系统只有16G，而且只运行MySQL，且MySQL只用InnoDB，那么为MySQL开12G，是最大限度地利用内存了。

另外InnoDB和 MyISAM 存储引擎不同， MyISAM 的key_buffer_size 只能缓存索引键，而innodb_buffer_pool_size 却可以缓存数据块和索引键。适当的增加这个参数的大小，可以有效的减少 InnoDB 类型的表的磁盘 I/O 。

当我们操作一个 InnoDB 表的时候，返回的所有数据或者去数据过程中用到的任何一个索引块，都会在这个内存区域中走一遭。

可以通过 (Innodb_buffer_pool_read_requests – Innodb_buffer_pool_reads) / Innodb_buffer_pool_read_requests * 100% 计算缓存命中率，并根据命中率来调整 innodb_buffer_pool_size 参数大小进行优化。值可以用以下命令查得：show status like 'Innodb_buffer_pool_read%';

比如查看当前系统中系统中

+---------------------------------------+---------+
| Innodb_buffer_pool_read_requests      | 1283826 |
| Innodb_buffer_pool_reads              | 519     |

其命中率99.959%=（1283826-519）/1283826*100%  命中率越高越好。