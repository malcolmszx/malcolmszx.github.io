---
layout: post                    # 使用的布局（不需要改）
title:  新闻公告类型             # 标题
subtitle:  Hello World, Hello Blog # 副标题
date:       2018-04-27              # 时间
author:     Malcolmszx              # 作者
header-img: img/post-bg-2015.jpg    # 这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               # 标签
    - Interface
---

### 创建新闻公告类型

- **请求uri**

  /bulletinType/create

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | name          | String        |    是         | 类型          | -             |     -         |
  | seq           | String        |    是         | 显示顺序      | -             |     -         |
  | insideShare   | String        |    是         | 内部分享 0 不允许 1 允许 | -  |     1        |
  | outsideShare  | String        |    是         | 外部分享 0 不允许 1 允许 | -  |     0        |
  | comment       | String        |    是         | 评论 0 不允许 1 允许 | -      |     -        |

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
- **请求成功，但是创建失败**
```
  {
      "code": 202,
      "msg": "该类型存在"
  }
```
- **备注**

  当创建的新闻公告类型已经存在时，创建失败，返回状态码code：202 msg:该类型存在

### 编辑新闻公告类型

- **请求uri**

  /bulletinType/editor

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | id            | String        |    是         | 新闻公告类型id | -             |     -         |
  | name          | String        |    否         | 类型          | -             |     -         |
  | seq           | String        |    否         | 显示顺序      | -             |     -         |
  | status        | String        |    否         | 0 禁用 1 启用 | -             |     1        |
  | insideShare   | String        |    否         | 内部分享 0 不允许 1 允许 | -   |     1        |
  | outsideShare  | String        |    否         | 外部分享 0 不允许 1 允许 | -   |     0        |
  | comment       | String        |    否         | 评论 0 不允许 1 允许 | -       |     -        |


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

### 获取新闻公告类型列表

- **请求uri**

  /bulletinType/getList

- **请求方式**

  get

  http://localhost:8099/bulletin/bulletinType/getList/{eid}

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101      |

- **返回正确JSON示例**
```
  {
    "code":200,
    "msg":"请求成功",
    "data":[
             {
                "id":"5ae92a4f29bbf603104abce9",
                "name":"员工发展",
                "insideShare":"1",
                "outsideShare":"0",
                "comment":"0",
                "status":"1",
                "seq":"2",
                "delete":"1",
                "creator":"5ae92a4f29bbf603904abce9",
                "creatorDate":1525229096,
                "eid":"236"
           }
         ]
  }
```

### 删除新闻公告类型

- **请求uri**

  /bulletinType/delete

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | id            | String        |    是         | 新闻公告类型id | -             |     -         |
  | name          | String        |    否         | 类型          | -             |     -         |

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
- **请求成功，但是删除失败**
```
  {
     "code": 200,
     "msg": "该分类下有新闻公告内容，暂不可删除，如需删除，请先移走该分类下的内容",
     "data": null
  }
```

### 更新新闻公告类型状态

- **请求uri**

  /bulletinType/updateStatus

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | id            | String        |    否         | 新闻公告类型id | -             |     -         |
  | status        | String        |    是         | 0 禁用 1 启用 | -            |     -        |

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
### 备注

有问题及时讨论，给你带来不便，抱歉！
