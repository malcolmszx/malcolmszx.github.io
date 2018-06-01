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

  /type/create

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
    "msg": "该类型存在",
    "data": null
  }
```
- **备注**

  当创建的新闻公告类型已经存在时，创建失败，返回状态码code：202 msg:该类型存在

### 编辑新闻公告类型

- **请求uri**

  /type/editor

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
  | status        | String        |    否         | 0 禁用 1 启用 | -             |     1         |
  | insideShare   | String        |    否         | 内部分享 0 不允许 1 允许 | -   |     1         |
  | outsideShare  | String        |    否         | 外部分享 0 不允许 1 允许 | -   |     0         |
  | comment       | String        |    否         | 评论 0 不允许 1 允许 | -       |     -         |


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
    "code": 205,
    "msg": "参数不正确",
    "data": null
  }
```

### 获取新闻公告类型列表

- **请求uri**

  /type/getList

- **请求方式**

  get

  http://localhost:8099/bulletin/type/getList/{eid}

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101      |

- **返回正确JSON示例**
```
  {
    "code": 200,
    "msg": "请求成功",
    "data": [
        {
            "id": "5af692ee29bbf633a03f6887",
            "name": "职级申请",
            "insideShare": "1",
            "outsideShare": "0",
            "comment": "0",
            "status": "1",
            "seq": "2",
            "delete": "1",
            "creator": "2cbe6aa9-f327-4d2c-b474-6c47ff34726e",
            "creatorDate": 1526108908492,
            "eid": "236"
        },
        {
            "id": "5af693c029bbf633a03f6888",
            "name": "职工蓝图",
            "insideShare": "1",
            "outsideShare": "0",
            "comment": "0",
            "status": "1",
            "seq": "3",
            "delete": "1",
            "creator": "2cbe6aa9-f327-4d2c-b474-6c47ff34726e",
            "creatorDate": 1526109120937,
            "eid": "236"
        }
    ]
}
```

### 删除新闻公告类型

- **请求uri**

  /type/delete

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

  /type/updateStatus

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

必填参数，端上严格按照规范。

### 创建新闻公告管理员

- **请求uri**

  admin/create

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | name          | String        |    是         | 管理员姓名     | -            |     -         |
  | oid           | String        |    是         | 管理员oid      | -            |     -         |

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

  admin/list

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101       |

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

  admin/delete

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | ids           |list           |    是         |管理员ids      | -             |      -         |

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

  admin/query

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -              |      236      |
  | name          | String        |    是         | 管理员姓名    | -              |    李         |

- **返回正确JSON示例**
```
  {
    "code": 200,
    "msg": "请求成功",
    "data": [
        {
            "id": "5aea747329bbf602349dcf5e",
            "eid": "236",
            "pubId": "XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",
            "oid": "5be82a4f29bbf603904abce9",
            "name": "李贵",
            "creatorOId": "5ae92a4f29bbf603904abcf5",
            "creatorName": "张航",
            "creatorDate": 1625228960,
            "status": "1"
        },
        {
            "id": "5af6aa4929bbf605d482456f",
            "eid": "236",
            "pubId": "XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",
            "oid": "6ac82a4f29bbf603904abce8",
            "name": "李大爷",
            "creatorOId": "2cbe6aa9-f327-4d2c-b474-6c47ff34726e",
            "creatorName": "系统管理员",
            "creatorDate": 1526114887409,
            "status": "1"
        }
    ]
}
```
- **备注**

  新闻公告公众号 pubid：XT-717062e8-8ee5-4873-a607-e8ccf4e8068f

### 新建新闻公告详情

- **请求uri**

  info/save

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | title         | String        |    是         | 标题          | -             |       -       |
  | subTitle        | String        |    是         | 副标题         | -            |       -     |
  | articleUrl    | String        |    是         | 文章url       | -             |       -       |
  | pic           | String        |    否         | 图片url       | -             |       -       |
  | bulletinMsgtype | String      |    是         | 公告内容类型   | -            |     -         |
  | bulletinType  | String        |    是         | 公告类型       | -            |     -         |
  | orderType     | String        |    是         | 显示顺序       | -            |     1         |
  | status        | String        |    是         | 0 草稿 1 发布  |       -      |       -       |
  | expireDate    | Date          |    否         | 过期时间        |        -      |  1526354989  |
  | attachments   | Json          |    否         | 附件Json对象数组 | -           |     -         |
  | type          | Json          |    是         | 公告类型Json对象 | -           |     -         |

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
- **返回错误JSON示例**
```
  {
      "code": 204,
      "msg": "用户不存在"
  }
```
- **返回错误参数JSON示例**
```
  {
      "code": 205,
      "msg": "参数不正确"
  }
```

- **备注**

  1. 参数：type  新闻公告类型的json, 创建新闻公告详情时异步请求获取其对象具体uri 参考新闻公告类型接口文档，
  2. 参数：attachments  新闻公告附件, 类型为json数组，
  3. 暂存、保存并发布复用同一个接口，修改status状态即可。

### 置顶或取消置顶(兼容批量)

- **请求uri**

  info/updateToporNo

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | id            | String        |    是         | 新闻公告id     | -             |      -      |
  | top           | String        |    是         | 0取消置顶 1置顶 |      -     |       -         |

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

支持批量处理，后端接收Json对象数组

### 删除新闻公告详情(兼容批量删除)

- **请求uri**

  info/delete

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | ids           | list        |    是         | 新闻公告ids     | -            |      -      |

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

### 条件查询新闻公告详情

- **请求uri**

  info/getListPageByCondition/{eid}

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id       | -             |      236      |
  | pageNumber    | int           |    是         | 页码           | -             |     -         |
  | pageSize      | int           |    是         | 页面大小       | -             |       -       |
  | title         | String        |    是         | 标题          | -             |       -       |
  | bulletinType  | String        |    是         | 公告类型       | -            |     -         |
  | status        | String        |    是         | 0 草稿 1 发布| -            |       -        |

- **返回正确JSON示例**
```
{
    "code":200,
    "msg":"请求成功",
    "data":{
        "content":[
                    {
                       "id":"5aebc35329bbf612bc09bc6b",
                       "title":"百度资讯发送消息",
                       "subTitle":null,
                       "author":"5ad5c3ec29bbf624b4784628",
                       "status":"1",
                       "expireDate":1525399807,
                       "url":null,
                       "content":null,
                       "pic":null,
                       "articleUrl":null,
                       "articleId":null,
                       "attachments":null,
                       "type":{
                                  "id":"9ad5c3ec29bbf624b4784628",
                                  "name":"员工发展",
                                  "insideShare":"1",
                                  "outsideShare":"0",
                                  "comment":null,
                                  "status":"1",
                                  "seq":null,
                                  "delete":"1",
                                  "creator":null,
                                  "creatorDate":null,
                                  "eid":"236"
                              },
                      "readnum":0,
                      "praisenum":0,
                      "creator":null,
                      "publishDate":1525399857,
                      "eid":"236",
                      "delete":"1",
                      "top":"0",
                      "orderType":"2",
                      "bulletinType":"员工发展",
                      "updateToporNodate":1525399957,
                      "bulletinMsgtype":"6"
                   }
                ],
        "totalPages":1,
        "totalElements":1,
        "last":true,
        "number":0,
        "size":20,
        "sort":[
                  {
                      "direction":"DESC",
                      "property":"publishDate",
                      "ignoreCase":false,
                      "nullHandling":"NATIVE",
                      "ascending":false,
                      "descending":true
                  }
              ],
        "numberOfElements":1,
        "first":true
     }
}
```
- **返回错误JSON示例**
```
  {
      "code": 204,
      "msg": "用户不存在"
  }
```

### 获取所有新闻公告详情

- **请求uri**

  info/getListByPage/{eid}?pageNumber=1&pageSize=20

- **请求方式**

  get

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id       | -             |      236      |
  | pageNumber    | int           |    是         | 页码           | -             |     -         |
  | pageSize      | int           |    是         | 页面大小       | -             |       -       |

- **返回正确JSON示例**
```
{
    "code":200,
    "msg":"请求成功",
    "data":{
        "content":[
                    {
                       "id":"5aebc35329bbf612bc09bc6b",
                       "title":"百度资讯发送消息",
                       "subTitle":null,
                       "author":"5ad5c3ec29bbf624b4784628",
                       "status":"1",
                       "expireDate":1525399807,
                       "url":null,
                       "content":null,
                       "pic":null,
                       "articleUrl":null,
                       "articleId":null,
                       "attachments":null,
                       "type":
                               {
                                  "id":"9ad5c3ec29bbf624b4784628",
                                  "name":"员工发展",
                                  "insideShare":"1",
                                  "outsideShare":"0",
                                  "comment":null,
                                  "status":"1",
                                  "seq":null,
                                  "delete":"1",
                                  "creator":null,
                                  "creatorDate":null,
                                  "eid":"236"
                              },
                      "readnum":0,
                      "praisenum":0,
                      "creator":null,
                      "publishDate":1525399857,
                      "eid":"236",
                      "delete":"1",
                      "top":"0",
                      "orderType":"2",
                      "bulletinType":"员工发展",
                      "updateToporNodate":1525399957,
                      "bulletinMsgtype":"6"
             }
         ],
        "totalPages":1,
        "totalElements":1,
        "last":true,
        "number":0,
        "size":20,
        "sort":[
                 {
                      "direction":"DESC",
                      "property":"publishDate",
                      "ignoreCase":false,
                      "nullHandling":"NATIVE",
                      "ascending":false,
                      "descending":true
                  }
              ],
        "numberOfElements":1,
        "first":true
     }
}
```
- **返回错误JSON示例**
```
  {
      "code": 204,
      "msg": "用户不存在"
  }
```

### 卡片加载最新6条新闻公告详情

- **请求uri**

  info/app/getLatestSix

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      236      |

 - **返回正确JSON示例**
   ```
  {
    "code": 200,
    "msg": "请求成功",
    "data": [
        {
            "id": "5af9575d29bbf628dc7779a8",
            "title": "百度资讯发送消息",
            "subTitle": null,
            "author": "系统管理员",
            "status": "1",
            "expireDate": null,
            "url": null,
            "content": null,
            "pic": null,
            "articleUrl": null,
            "articleId": null,
            "attachments": null,
            "type": {
                "id": "9ad5c3ec29bbf624b4784628",
                "name": "员工发展",
                "insideShare": "1",
                "outsideShare": "0",
                "comment": null,
                "status": "1",
                "seq": null,
                "delete": "1",
                "creator": null,
                "creatorDate": null,
                "eid": "236"
            },
            "readnum": 0,
            "praisenum": 0,
            "creator": "2cbe6aa9-f327-4d2c-b474-6c47ff34726e",
            "publishDate": 1526290269185,
            "eid": "236",
            "delete": "1",
            "top": "0",
            "orderType": "2",
            "bulletinType": "员工发展",
            "updateToporNodate": 1526290269185,
            "bulletinMsgtype": "6"
        },
        {
            "id": "5aebc35329bbf612bc09bc6b",
            "title": "百度资讯发送消息",
            "subTitle": null,
            "author": "5ad5c3ec29bbf624b4784628",
            "status": "1",
            "expireDate": 1579362199807,
            "url": null,
            "content": null,
            "pic": null,
            "articleUrl": null,
            "articleId": null,
            "attachments": null,
            "type": {
                "id": "5ae92a4f29bbf603104abce9",
                "name": "员工发展",
                "insideShare": "1",
                "outsideShare": "0",
                "comment": null,
                "status": "1",
                "seq": null,
                "delete": "1",
                "creator": null,
                "creatorDate": null,
                "eid": "236"
            },
            "readnum": 0,
            "praisenum": 0,
            "creator": null,
            "publishDate": 1525399857,
            "eid": "236",
            "delete": "1",
            "top": "0",
            "orderType": "2",
            "bulletinType": "员工发展",
            "updateToporNodate": 1525399957,
            "bulletinMsgtype": "6"
        }
    ]
}
```
- **返回错误JSON示例**
```
  {
      "code": 204,
      "msg": "用户不存在"
  }
```

### 懒惰加载最新新闻公告详情

- **请求uri**

  info/app/getLatest

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | updown        | boolean       |    是         | true 最新 false 旧数据    | -           |  -   |
  | publishDate   | String        |    是         | 发布时间       | -           |  1525399857   |

 - **返回正确JSON示例**
   ```
   {
       "code": 200,
       "msg": "请求成功",
       "data": [
                 {
                     "id": "5aebc35329bbf612bc09bc6b",
                     "title": "百度资讯发送消息",
                     "subTitle": null,
                     "author": "5ad5c3ec29bbf624b4784628",
                     "status": "1",
                     "expireDate": 1525399807,
                     "url": null,
                     "content": null,
                     "pic": null,
                     "articleUrl": null,
                     "articleId": null,
                     "attachments": null,
                     "type":
                              {
                                  "id": "9ad5c3ec29bbf624b4784628",
                                  "name": "员工发展",
                                  "insideShare": "1",
                                  "outsideShare": "0",
                                  "comment": null,
                                  "status": "1",
                                  "seq": null,
                                  "delete": "1",
                                  "creator": null,
                                  "creatorDate": null,
                                  "eid": "236"
                              },
                      "readnum": 0,
                      "praisenum": 0,
                      "creator": null,
                      "publishDate": 1525399857,
                      "eid": "236",
                      "delete": "1",
                      "top": "0",
                      "orderType": "2",
                      "bulletinType": "员工发展",
                      "updateToporNodate": 1525399957,
                      "bulletinMsgtype": "6"
                 }
             ]
  }
```
- **返回错误JSON示例**
```
  {
      "code": 204,
      "msg": "用户不存在"
  }
```
- **返回错误参数JSON示例**
```
  {
      "code": 205,
      "msg": "参数不正确"
  }
```

### 懒惰加载某类新闻公告详情

- **请求uri**

  info/app/type/getLatest

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | bulletinType  | String        |    是         | 公告类型       | -            |     -         |
  | updown        | boolean       |    是         | true 最新 false 旧数据    | -           |  -   |
  | publishDate   | String        |    是         | 发布时间       | -            |  1525399857 |

 - **返回正确JSON示例**
   ```
   {
       "code": 200,
       "msg": "请求成功",
       "data": [
                 {
                     "id": "5aebc35329bbf612bc09bc6b",
                     "title": "百度资讯发送消息",
                     "subTitle": null,
                     "author": "5ad5c3ec29bbf624b4784628",
                     "status": "1",
                     "expireDate": 1525399807,
                     "url": null,
                     "content": null,
                     "pic": null,
                     "articleUrl": null,
                     "articleId": null,
                     "attachments": null,
                     "type":
                              {
                                "id": "9ad5c3ec29bbf624b4784628",
                                "name": "员工发展",
                                "insideShare": "1",
                                "outsideShare": "0",
                                "comment": null,
                                "status": "1",
                                "seq": null,
                                "delete": "1",
                                "creator": null,
                                "creatorDate": null,
                                "eid": "236"
                                    },
                    "readnum": 0,
                    "praisenum": 0,
                    "creator": null,
                    "publishDate": 1525399857,
                    "eid": "236",
                    "delete": "1",
                    "top": "0",
                    "orderType": "2",
                    "bulletinType": "员工发展",
                    "updateToporNodate": 1525399957,
                    "bulletinMsgtype": "6"
                }
            ]
  }
  ```
  - **返回错误JSON示例**
```
  {
      "code": 204,
      "msg": "用户不存在"
  }
```
- **返回错误参数JSON示例**
```
  {
      "code": 205,
      "msg": "参数不正确"
  }
```
### 添加新闻公告留言

- **请求uri**

  comment/save

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type", "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | bullentinId   | String        |    是         | 新闻公告id     | -  |- |
  | content       | String        |    是         | 评论内容       | -            |     -       |

- **返回正确JSON示例**
  ```
  {
      "code": 200,
      "msg": "请求成功"
      "data": null
  }
  ```
- **返回错误JSON示例**  
  ```
  {
      "code": 204,
      "msg": "用户不存在"
  }
  ```
- **返回错误参数JSON示例**  
  ```
  {
      "code": 205,
      "msg": "参数不正确"
  }
  ```

### 回复新闻公告留言

- **请求uri**

  comment/reply
  
- **请求方式**

  post

- **请求头**

  "key" : "Content-Type", "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | bullentinId   | String        |    是         | 新闻公告id     | -  |- |
  | content       | String        |    是         | 评论内容       | -            |     -       |
  | toUsername    | String        |    是         | 回复的人员姓名  | -  |- |
  | toCommentId   | String        |    是         | 回复的评论id   | -            |     -        |
  | toPersonId    | String        |    是         | 回复的人员oid  | -            |     -        |

- **返回正确JSON示例**
  ```
  {
      "code": 200,
      "msg": "请求成功"
      "data": null
  }
  ```
- **返回错误JSON示例**  
  ```
  {
      "code": 204,
      "msg": "用户不存在"
  }
  ```
- **返回错误参数JSON示例**  
  ```
  {
      "code": 205,
      "msg": "参数不正确"
  }
  ```
- **备注**

  1、留言参数与回复留言参数不一致，回复留言必填最后三个变量：toUsername、toCommentId
    、toPersonId

### 点赞/取消新闻公告留言

- **请求uri**

  comment/updateParise

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | commentId     | String        |    是         | 评论id         | -             |      -      |
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
- **返回错误参数JSON示例**  
  ```
  {
      "code": 205,
      "msg": "参数不正确"
  }
  ```

### 删除新闻公告留言

- **请求uri**

  comment/delete/{bulletinId}/{commentId}

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | bullentinId   | String        |    是         | 新闻公告id     | -  |- |
  | commentId     | String        |    是         | 评论id         | -             |      -     |

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
      "code": 205,
      "msg": "参数不正确"
  }
  ```
- **返回错误JSON示例**  
  ```
  {
      "code": 204,
      "msg": "用户不存在"
  }
  ```

### 分页获取评论列表

- **请求uri**

  comment/queryList

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id       | -             |      101      |
  | bullentinId   | String        |    是         | 新闻公告id     | -  |- |
  | pageNumber    | int           |    是         | 页码           | -             |     -         |
  | pageSize      | int           |    是         | 页面大小       | -             |       -       |

- **返回正确JSON示例**
```
  {  
    "code": 200,  
    "msg": "请求成功",  
    "data": {  
        "content": [  
            {  
                "id": "5aefedaa29bbf618b4373fe2",  
                "bulletinId": "8ad593ec29bbf624b4784648",  
                "username": "huangxiaoming",  
                "toUsername": null,  
                "content": "测试新闻公告留言",  
                "delete": false,  
                "eid": "236",  
                "personId": "6ad5c3ec29bbf624b4784628",  
                "photoUrl": null,  
                "createTime": 1525672959,  
                "deletePersonId": null,  
                "deleteTime": null,  
                "toCommentId": "",  
                "toPersonId": null,  
                "partnerType": false,  
                "praise": null,  
                "commentPraiseNum": 0,  
                "praiseList": [],  
                "replys": [  
                    {  
                        "id": "5aefedaa29bbf618b4373fe2",  
                        "bulletinId": "8ad593ec29bbf624b4784648",  
                        "username": "dengqw",  
                        "toUsername": "huangxiaoming",  
                        "content": "测试回复新闻公告留言",  
                        "delete": false,  
                        "eid": "236",  
                        "personId": "6ad5c3ec29bbf624b4784628",  
                        "photoUrl": null,  
                        "createTime": 1525672959,  
                        "deletePersonId": null,  
                        "deleteTime": null,  
                        "toCommentId": "5aefedaa29bbf618b4373fe2",  
                        "toPersonId": "6ad5c3ec29bbf624b4784628",  
                        "partnerType": false,  
                        "praise": null,  
                        "commentPraiseNum": 0,  
                        "praiseList": [],  
                        "replys": null  
                    }  
                ]  
            }  
        ],  
        "totalPages": 1,  
        "totalElements": 1,  
        "last": true,  
        "number": 0,  
        "size": 20,  
        "sort": [  
            {  
                "direction": "DESC",  
                "property": "createTime",  
                "ignoreCase": false,  
                "nullHandling": "NATIVE",  
                "ascending": false,  
                "descending": true  
            }  
        ],  
        "numberOfElements": 1,  
        "first": true  
    }  
}  
```

- **备注**

  1、返回的json示例修改中，有疑问及时交流。。。

  ### 添加阅读数

- **请求uri**

  browsePraise/updateBrowse

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | bullentinId   | String        |    是         | 新闻公告id     |      -        |         -     |

- **返回正确JSON示例**
  ```
    {
        "code": 200,
        "msg": "请求成功",
        "data": null
    }
  ```

### 添加/取消点赞数

- **请求uri**

  browsePraise/updatePraise

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/son"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | bullentinId   | String        |    是         | 新闻公告id     | -  |- |
  | addordelete   | boolean       |    是         | true 点赞 false 取消 | -       |      true     |

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
