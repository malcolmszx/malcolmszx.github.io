---
layout:  post
title: 新闻公告管理员
subtitle: admin eiditor
date:   2018-05-03
author:   BY Malcolmszx
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - interface
---

### 创建新闻公告管理员

- **请求uri**

  bulletinAdmin/create

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | id            | String        |    否         | 管理员id      | -             |     -         |
  | eid           | String        |    是         | 工作圈id      | -             |      101      |
  | pubId         | String        |    是         | 公共号id | -  |             -                 |
  | name          | String        |    是         | 管理员姓名    | -            |     -         |
  | oid           | String        |    是         | 管理员oid     | -            |     -         |
  | status        | String        |    是         | 0为删除 1为正常 | -            |     1        |
  | creatorOId    | String        |    是         | 创建人oID      | -             |     -        |
  | creatorName   | String        |    是         | 创建人姓名     |        -      |     -        |
  | creatorDate   | Date          |    是         | 创建日期       | -             |     -        |

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
- **备注**

  兼容添加多个新闻公告管理员,后端接收json数组.

### 获取新闻公告管理员列表

- **请求uri**

  bulletinAdmin/list

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101      |
  | pubId         | String        |    是         | 公共号id | -  |- |
  | status        | String        |    是         | 0为删除 1为正常 | -            |     1        |

- **返回正确JSON示例**
  ```
    {
      "code": 200,
      "msg": "请求成功",
      "data": [
                {
                  "eid": "236",
                  "pubId": "XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",
                  "id": "5aea747329bbf602349dcf5d",
                  "oid": "5ae92a4f29bbf603904abce9",
                  "name": "黄小明",
                  "creatorOId": "5ae92a4f29bbf603904abcf5",
                  "creatorName": "张航",
                  "creatorDate": 1525229096,
                  "status": "1"
               },
               {
                  "eid": "236",
                  "pubId": "XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",
                  "id": "5aea747329bbf602349dcf5e",
                  "oid": "5be82a4f29bbf603904abce9",
                  "name": "李贵",
                  "creatorOId": "5ae92a4f29bbf603904abcf5",
                  "creatorName": "张航",
                  "creatorDate": 1625228096,
                  "status": "1"
              }
           ]
  }
```
- **返回错误JSON示例**
```
  {
      "code": 201,
      "msg": "请求失败"
  }
```  

### 删除新闻公告管理员

- **请求uri**

  bulletinAdmin/delete

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101      |
  | pubId         | String        |    是         | 公共号id      | -             |  -            |

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
### 查询新闻公告管理员

- **请求uri**

  bulletinAdmin/query

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101      |
  | pubId         | String        |    是         | 公共号id | -  |         -                     |
  | name          | String        |    是         | 管理员姓名    | -            |     -         |
  | status        | String        |    是         | 0为删除 1为正常 | -            |     1        |

- **返回正确JSON示例**
```
  {
    "code": 200,
    "msg": "请求成功",
    "data": [
              {
                  "eid": "236",
                  "pubId": "XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",
                  "id": "5aea747329bbf602349dcf5d",
                  "oid": "5ae92a4f29bbf603904abce9",
                  "name": "黄小明",
                  "creatorOId": "5ae92a4f29bbf603904abcf5",
                  "creatorName": "张航",
                  "creatorDate": 1525229960,
                   "status": "0"
             }
           ]
  }
```
- **备注**

  新闻公告公众号 pubid：XT-717062e8-8ee5-4873-a607-e8ccf4e8068f
