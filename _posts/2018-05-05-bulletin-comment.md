---
layout:     post
title: 新闻公告评论
subtitle: editor and so on
date:       2018-05-05
author:     BY Malcolmszx
header-img: img/post-bg-debug.png
catalog: true
tags:
    - interface
---
### 添加新闻公告评论

- **请求uri**

  bulletinComment/save

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id       | -             |      101      |
  | bullentinId   | String        |    是         | 新闻公告id     | -  |- |
  | content       | String        |    是         | 评论内容       | -            |     1        |
  | createTime    | String        |    是         | 评论时间       | -            |     1        |

- **返回正确JSON示例**
  ```
  {
      "code": 200,
      "msg": "请求成功",
      "data": null
  }
  ```
- **返回错误JSON示例**  
  ```
  {
      "code": 201,
      "msg": "请求失败"
  }
  ```
### 点赞/取消新闻公告评论

- **请求uri**

  bulletinComment/updateParise

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | commentId     | String        |    是         | 评论id         | -             |      101      |
  | addOrdelete   | String        |    是         | true 添加 false 取消| -  |- |

- **返回正确JSON示例**
  ```
  {
      "code": 200,
      "msg": "请求成功",
      "data": null
  }
  ```
- **返回错误JSON示例**
  ```
  {
      "code": 201,
      "msg": "请求失败"
  }
  ```
### 删除新闻公告评论

- **请求uri**

  bulletinComment/delete/{bulletinId}/{commentId}

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id       | -             |      101      |
  | bullentinId   | String        |    是         | 新闻公告id     | -  |- |
  | commentId     | String        |    是         | 评论id         | -             |      101      |

- **返回正确JSON示例**
  ```
  {
      "code": 200,
      "msg": "请求成功",
      "data": null
  }
  ````   
- **返回错误JSON示例**
  ```
  {
      "code": 201,
      "msg": "请求失败"
  }
  ```
