---
layout:     post
title: 新闻公告阅读点赞
subtitle: editor and so on
date:       2018-05-06
author:     BY Malcolmszx
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
    - interface
---

### 添加阅读数

- **请求uri**

  browsePraise/updateBrowse

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/son"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 圈子id         | -             |      101      |
  | bullentinId   | String        |    是         | 新闻公告id     | -  |- |

- 