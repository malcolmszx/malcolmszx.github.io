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

合理地设置thread_concurrency的值，对mysql的性能影响很大，尤其在多个cpu(多核)的情况下，该值设置不当会直接导致mysql不能充分利用系统资源（多cpu多核），一般情况下，thread_concurrentcy的值，设置为cpu核数的两倍,查看系统当前thread_concurrency默认配置命令：show variables like 'thread_concurrency' ;

#### max_connections

max_connections参数指的是MySql的最大连接数，如果服务器的并发连接请求量比较大，建议调高此值，以增加并行连接数量，当然这建立在机器能支撑的情况下，因为如果连接数越多，介于MySql会为每个连接提供连接缓冲区，就会开销越多的内存，所以要适当调整该值，不能盲目提高设值。可以过'conn%'通配符查看当前状态的连接数量，以定夺该值的大小。注意：MySQL服务器允许的最大连接数16384;
查看系统当前最大连接数：show variables like 'max_connections';

#### back_log

如果MySql的连接数据达到max_connections时，新来的请求将会被存在堆栈中，以等待某一连接释放资源，该堆栈的数量即back_log，如果等待连接的数量超过back_log，将不被授予连接资源。将会报：unauthenticated user xxx.xxx.xxx.xxx  NULL  Connect  NULL  login  NULL ，等待连接进程时，back_log值不能超过TCP/IP连接的侦听队列的大小，若超过则无效。

查看当前系统的TCP/IP连接的侦听队列的大小命令：cat /proc/sys/net/ipv4/tcp_max_syn_backlog。 

对于Linux系统推荐设置为小于512的整数，修改系统内核参数。

- [修改系统内核参](http://www.51testing.com/html/64/n-810764.html)

查看mysql 当前系统默认back_log值，命令：show variables like 'back_log';

### MySQL缓存变量介绍及修改（全局参数）

数据库属于IO密集型的应用程序，职责是数据的管理及存储。从内存中读取一个数据库的时间是微秒级别，而从一块普通硬盘上读取一个IO是在毫秒级别，二者相差3个数量级。

因此，要优化数据库，首先第一步需要优化的就是IO，尽可能将磁盘IO转化为内存IO。

从MySQL数据库IO相关参数(缓存参数)的角度可以通过哪些参数进行IO优化？

#### innodb_buffer_pool_size 

innodb_buffer_pool_size:主要针对InnoDB表性能影响最大的一个参数。功能与Key_buffer_size一样。InnoDB占用的内存，除innodb_buffer_pool_size用于存储页面缓存数据外，另外正常情况下还有大约8%开销，主要用在每个缓存页帧的描述、adaptive hash等数据结构，如果不是安全关闭，启动时还要恢复的话，还要另开大约12%的内存用于恢复，两者相加就有差不多21%的开销。
 
假设：12G的innodb_buffer_pool_size，最多的时候InnoDB就可能占用到14.5G的内存。若系统只有16G，而且只运行MySQL，且MySQL只用InnoDB，那么为MySQL开12G，是最大限度地利用内存了。

另外InnoDB 和MyISAM 存储引擎不同， MyISAM 的key_buffer_size 只能缓存索引键，而innodb_buffer_pool_size 却可以缓存数据块和索引键。适当的增加这个参数的大小，可以有效的减少 InnoDB 类型的表的磁盘 I/O 。

当我们操作一个 InnoDB 表的时候，返回的所有数据或者删除数据过程中用到的任何一个索引块，都会在这个内存区域中走一遭。

可以通过 (Innodb_buffer_pool_read_requests – Innodb_buffer_pool_reads) / Innodb_buffer_pool_read_requests * 100% 计算缓存命中率，并根据命中率来调整 innodb_buffer_pool_size 参数大小进行优化。

值可以用以下命令查得：show status like 'Innodb_buffer_pool_read%';

比如查看当前系统中系统中

| Variable_name   |  Value  |
| ----------------|--- ----:|
| Innodb_buffer_pool_read_requests      | 1283826 |
| Innodb_buffer_pool_reads              | 519     |

其命中率99.959% =（1283826-519）/1283826 * 100%  命中率越高越好。

#### key_buffer_size 

key_buffer_size：索引块的缓冲区大小，增加它可得到更好处理的索引。对 MyISAM表性能影响最大的一个参数。如果你使它太大，系统将开始换页并且真的变慢了。严格说是它决定了数据库索引处理的速度，尤其是索引读的速度。对于内存在4GB左右的服务器该参数可设置为256M或384M。

怎么才能知道key_buffer_size的设置是否合理呢？

一般可以检查状态值Key_read_requests和Key_reads，比例key_reads / key_read_requests应该尽可能的低，比如1:100，1:1000 ，1:10000。

其值可以用以下命令查得：show status like 'key_read%';

比如查看系统当前key_read和key_read_request值为：

| Variable_name   |  Value  |
| ----------------|--- ----:|
| Key_read_requests | 28535 |
| Key_reads         | 269   |

可知道有28535个请求，有269个请求在内存中没有找到直接从硬盘读取索引。

未命中缓存的概率为：0.94%=269/28535*100%.  一般未命中概率在0.1之下比较好。目前已远远大于0.1，证明效果不好。若命中率在0.01以下，则建议适当的修改key_buffer_size值。

- [InnoDB与MyISAM的六大区别](https://blog.csdn.net/paul342/article/details/49382667)

- [查看存储引擎介绍](http://kb.cnblogs.com/page/99810)

MyISAM、InnoDB、MyISAM Merge引擎、InnoDB、memory(heap)、archive

#### query_cache_size

query_cache_size: 主要用来缓存MySQL中的ResultSet，也就是一条SQL语句执行的结果集，所以仅仅只能针对select语句。

当我们打开了Query Cache功能，MySQL在接受到一条select语句的请求后，如果该语句满足Query Cache的要求(未显式说明不允许使用Query Cache，或者已经显式申明需要使用Query Cache)，MySQL会直接根据预先设定好的HASH算法将接受到的select语句以字符串方式进行hash，然后到Query Cache中直接查找是否已经缓存。

如果已经在缓存中，该select请求就会直接将数据返回，极大的提高性能。根据MySQL用户手册，使用查询缓冲最多可以达到238%的效率。

当然，Query Cache也有一个致命的缺陷，当某个表的数据有任何任何变化，都会导致所有引用了该表的select语句在Query Cache中的缓存数据失效。所以，当我们的数据变化非常频繁的情况下，使用Query Cache可能会得不偿失。

Query Cache的使用需要多个参数配合，其中最为关键的是query_cache_size和query_cache_type，前者设置用于缓存 ResultSet的内存大小，后者设置在何场景下使用Query Cache。

在以往的经验来看，如果不是用来缓存基本不变的数据的MySQL数据库，query_cache_size：一般256MB是一个比较合适的大小。

当然，这可以通过计算Query Cache的命中率(Qcache_hits/(Qcache_hits+Qcache_inserts)*100))来进行调整。

query_cache_type可以设置为0(OFF)，1(ON)或者2(DEMOND)，分别表示完全不使用query cache，除显式要求不使用query cache (使用sql_no_cache)之外的所有的select都使用query cache，只有显示要求才使用query cache(使用sql_cache)。如果Qcache_lowmem_prunes的值非常大，则表明经常出现缓冲. 如果Qcache_hits的值也非常大，则表明查询缓冲使用非常频繁，此时需要增加缓冲大小；

根据命中率(Qcache_hits/(Qcache_hits+Qcache_inserts)*100))进行调整，一般不建议太大，256MB可能已经差不多了，大型的配置型静态数据可适当调大.

可以通过命令：show status like 'Qcache_%';查看目前系统Query catch使用大小

| Variable_name   |  Value  |
| ----------------|--- ----:|
| Qcache_hits             | 1892463  |
| Qcache_inserts          | 35627  |

命中率98.17% = 1892463 / (1892463 +35627 ) * 100

### MySQL缓存变量介绍及修改（局部参数） 

#### read_buffer_size

read_buffer_size 是MySql读入缓冲区大小。对表进行顺序扫描的请求将分配一个读入缓冲区，MySql会为它分配一段内存缓冲区。read_buffer_size变量控制这一缓冲区的大小。如果对表的顺序扫描请求非常频繁，并且你认为频繁扫描进行得太慢，可以通过增加该变量值以及内存缓冲区大小提高其性能。

#### sort_buffer_size

sort_buffer_size是MySql执行排序使用的缓冲大小。如果想要增加ORDER BY的速度，首先看是否可以让MySQL使用索引而不是额外的排序阶段。如果不能，可以尝试增加sort_buffer_size变量的大小。

####  read_rnd_buffer_size

read_rnd_buffer_size 是MySql的随机读缓冲区大小。当按任意顺序读取行时(例如，按照排序顺序)，将分配一个随机读缓存区。进行排序查询时，MySql会首先扫描一遍该缓冲，以避免磁盘搜索，提高查询速度，如果需要排序大量数据，可适当调高该值。但MySql会为每个客户连接发放该缓冲空间，所以应尽量适当设置该值，以避免内存开销过大。

#### tmp_table_size

tmp_table_size是MySql的heap （堆积）表缓冲大小。所有联合在一个DML指令内完成，并且大多数联合甚至可以不用临时表即可以完成。大多数临时表是基于内存的(HEAP)表。具有大的记录长度的临时表 (所有列的长度的和)或包含BLOB列的表存储在硬盘上。如果某个内部heap（堆积）表大小超过tmp_table_size，MySQL可以根据需要自动将内存中的heap表改为基于硬盘的MyISAM表。还可以通过设置tmp_table_size选项来增加临时表的大小。也就是说，如果调高该值，MySql同时将增加heap表的大小，可达到提高联接查询速度的效果。

#### record_buffer

record_buffer每个进行一个顺序扫描的线程为其扫描的每张表分配这个大小的一个缓冲区。如果你做很多顺序扫描，你可能想要增加该值。默认数值是131072(128K)

### 其他

#### thread_cache_size 

默认的thread_cache_size=8，但是看到好多配置的样例里的值一般是32，64，甚至是128，感觉这个参数对优化应该有帮助，于是查了下：
根据调查发现以上服务器线程缓存thread_cache_size没有进行设置，或者设置过小,这个值表示可以重新利用保存在缓存中线程的数量,当断开连接时如果缓存中还有空间,那么客户端的线程将被放到缓存中,如果线程重新被请求，那么请求将从缓存中读取,如果缓存中是空的或者是新的请求，那么这个线程将被重新创建,如果有很多新的线程，增加这个值可以改善系统性能.通过比较 Connections 和 Threads_created 状态的变量，可以看到这个变量的作用。(–>表示要调整的值)   根据物理内存设置规则如下：
1G —> 8
2G —> 16
3G —> 32     >3G —> 64

  mysql> show status like 'thread%';

| Variable_name   |  Value  |  describle   |
| ----------------|:--- ----:|--- ----:|
| Threads_cached    | 0     | 当前被缓存的空闲线程的数量 |
| Threads_connected | 1     | 正在使用（处于连接状态）的线程 |
| Threads_created   | 1498  | 服务启动以来，创建了多少个线程 | 
| Threads_running   | 1     | 正在忙的线程（正在查询数据，传输数据等等操作）|

查看开机起来数据库被连接了多少次？

mysql> show status like '%connection%';

| Variable_name   |  Value  |  describle  |
| ----------------|:--- ----:|--- ----:|
| Connections          | 1504  | 服务启动以来，历史连接数  |
| Max_used_connections | 2     |   - |

通过连接线程池的命中率来判断设置值是否合适？命中率超过90%以上,设定合理。

 (Connections -  Threads_created) / Connections * 100 %

#### table_cache

table_cache指定表高速缓存的大小。每当MySQL访问一个表时，如果在表缓冲区中还有空间，该表就被打开并放入其中，这样可以更快地访问表内容。通过检查峰值时间的状态值Open_tables和Opened_tables，可以决定是否需要增加table_cache的值。如果你发现open_tables等于table_cache，并且opened_tables在不断增长，那么你就需要增加table_cache的值了（上述状态值可以使用SHOW STATUS LIKE ‘Open%tables’获得）。注意，不能盲目地把table_cache设置成很大的值。如果设置得太高，可能会造成文件描述符不足，从而造成性能不稳定或者连接失败。

SHOW STATUS LIKE 'Open%tables';

| Variable_name   |  Value  |
| ----------------|--- ----:|
| Open_tables   | 356   |
| Opened_tables | 0     |

2 rows in set (0.00 sec)

open_tables表示当前打开的表缓存数，如果执行flush tables操作，则此系统会关闭一些当前没有使用的表缓存而使得此状态值减小；

opend_tables表示曾经打开的表缓存数，会一直进行累加，如果执行flush tables操作，值不会减小。

在mysql默认安装情况下，table_cache的值在2G内存以下的机器中的值默认时256到512，如果机器有4G内存,则默认这个值 是2048，但这决意味着机器内存越大，这个值应该越大，因为table_cache加大后，使得mysql对SQL响应的速度更快了，不可避免的会产生 更多的死锁（dead lock），这样反而使得数据库整个一套操作慢了下来，严重影响性能。所以平时维护中还是要根据库的实际情况去作出判断，找到最适合你维护的库的 table_cache值。

由于MySQL是多线程的机制,为了提高性能,每个线程都是独自打开自己需要的表的文件描 述符,而不是通过共享已经打开的.针对不同存储引擎处理的方法当然也不一样

在myisam表引擎中,数据文件的描述符 (descriptor)是不共享的,但是索引文件的描述符却是所有线程共享的.Innodb中和使用表空间类型有关,假如是共享表空间那么实际就一个数 据文件,当然占用的数据文件描述符就会比独立表空间少.
mysql手册上给的建议大小 是:table_cache=max_connections*n

n表示查询语句中最大表数, 还需要为临时表和文件保留一些额外的文件描述符。

这个数据遭到很多质疑,table_cache够用就好,检查 Opened_tables值,如果这个值很大,或增长很快那么你就得考虑加大table_cache了.

table_cache：所有线程打开的表的数目。增大该值可以增加mysqld需要的文件描述符的数量。默认值是64.