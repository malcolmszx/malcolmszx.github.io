---
layout:     post
title:  如何避免MyBatis缓存带来的脏数据
subtitle:  MyBatis缓存机制
date:       2018-07-14
author:     BY Malcolmszx@gmail.com
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - MyBatis
    - Spring Boot
---

## 前沿

MyBatis是常见的Java数据库访问层框架。在日常工作中，开发人员多数情况下是使用MyBatis的默认缓存配置，但是MyBatis缓存机制有一些不
足之处，在使用中容易引起脏数据，形成一些潜在的隐患。业务开发中也经常处理过一些由于MyBatis缓存引发的开发问题，带着个人的兴趣，希
望从应用及源码的角度为读者梳理MyBatis缓存机制。本次分析中涉及到的代码和数据库表均放在GitHub上的地址：
[https://github.com/kailuncen/mybatis-cache-demo](https://github.com/kailuncen/mybatis-cache-demo)

### 一级缓存

#### 一级缓存概要

MyBatis开启一次和数据库的会话，MyBatis会创建出一个SqlSession对象表示一次数据库会话。在对数据库的一次会话中，有可能会反复地执行完全相同的查询语句，如果不采取一些措施的话，每一次查询都会查询一次数据库,而我们在极短的时间内做了完全相同的查询，那么它们的结果极有可能完全相同，由于查询一次数据库的代价很大，这有可能造成很大的资源浪费。

为了解决这一问题，减少资源的浪费，MyBatis会在表示会话的SqlSession对象中建立一个简单的缓存，将每次查询到的结果结果缓存起来，当下次查询的时候，如果判断先前有个完全一样的查询，会直接从缓存中直接将结果取出，返回给用户，不需要再进行一次数据库查询了。

如下图所示，MyBatis会在一次会话的表示----一个SqlSession对象中创建一个本地缓存(local cache)，对于每一次查询，都会尝试根据查询的条件去本地缓存中查找是否在缓存中，如果在缓存中，就直接从缓存中取出，然后返回给用户；否则，从数据库读取数据，将查询结果存入缓存并返回给用户。

![](http://misc.linkedkeeper.com/misc/img/blog/201709/linkedkeeper0_38e2dcb4-04af-4ffe-89ed-4fef7ad99424.jpg)

#### 一级缓存配置 

一级缓存的范围有SESSION和STATEMENT两种，默认是SESSION，如果不想使用一级缓存，可以把一级缓存的范围指定为STATEMENT，这样每次执行完一个Mapper中的语句后都会将一级缓存清除。 如果需要更改一级缓存的范围，可以在Mybatis的配置文件中，在下通过localCacheScope指定。

``` java 
<settings>
    <setting name="localCacheScope" value="STATEMENT"/>
</settings>
``` 

当Mybatis整合Spring后，直接通过Spring注入Mapper的形式，如果不是在同一个事务中每个Mapper的每次查询操作都对应一个全新的SqlSession实例，这个时候就不会有一级缓存的命中，但是在同一个事务中时共用的是同一个SqlSession。 
如有需要可以启用二级缓存。

#### 注意

- MyBatis一级缓存的生命周期和SqlSession一致。
- MyBatis同一个SqlSession中的增、删、改都会清空一级缓存。
- MyBatis一级缓存内部设计简单，只是一个没有容量限定的HashMap，在缓存的功能性上有所欠缺。
- MyBatis的一级缓存最大范围是SqlSession内部，有多个SqlSession或者分布式的环境下，数据库写操作会引起脏数据，建议设定缓存级别为Statement。

### 二级缓存

#### 二级缓存概要

在上文中提到的一级缓存中，其最大的共享范围就是一个SqlSession内部，如果多个SqlSession之间需要共享缓存，则需要使用到二级缓存。开启二级缓存后，会使用CachingExecutor装饰Executor，进入一级缓存的查询流程前，先在CachingExecutor进行二级缓存的查询。二级缓存开启后，同一个namespace下的所有操作语句，都影响着同一个Cache，即二级缓存被多个SqlSession共享，是一个全局的变量。当开启缓存后，数据的查询执行的流程就是 二级缓存 -> 一级缓存 -> 数据库。

#### 二级缓存配置 
``` java
<settings>
  <setting name="cacheEnabled" value="false" />
</settings>
```

要使用二级缓存除了上面一个配置外，我们还需要在我们每个DAO对应的Mapper.xml文件中定义需要使用的cache

``` java 
<mapper namespace="...UserMapper">
    <cache/><!-- 加上该句即可，使用默认配置、还有另外一种方式，在后面写出 -->
    ...
</mapper>
```

#### 注意

- MyBatis的二级缓存相对于一级缓存来说，实现了SqlSession之间缓存数据的共享，同时粒度更加的细，能够到namespace级别，通过Cache接口实现类不同的组合，对Cache的可控性也更强。
- MyBatis在多表查询时，极大可能会出现脏数据，有设计上的缺陷，安全使用二级缓存的条件比较苛刻。
- 在分布式环境下，由于默认的MyBatis Cache实现都是基于本地的，分布式环境下必然会出现读取到脏数据，需要使用集中式缓存将MyBatis的Cache接口实现，有一定的开发成本，直接使用Redis,Memcached等分布式缓存可能成本更低，安全性也更高。