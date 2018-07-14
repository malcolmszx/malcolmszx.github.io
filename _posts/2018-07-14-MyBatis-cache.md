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

