---
layout:     post
title: 新闻公告详情
subtitle: editor and so on
date:       2018-05-04
author:     BY Malcolmszx
header-img: img/post-bg-debug.png
catalog: true
tags:
    - interface
---
### 新建新闻公告详情

- **请求uri**

  bulletinInfo/save

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101      |
  | author        | String        |    是         | 创建人的 oid  | -             |     -         |
  | title         | String        |    是         | 标题          | -             |       -       |
  | bulletinMsgtype | String      |    是         | 公告内容类型   | -            |     -         |
  | bulletinType  | String        |    是         | 公告类型       | -            |     -         |
  | orderType     | String        |    是         | 显示顺序       | -            |     1         |
  | status        | String        |    是         | 0为草稿 1为发布| -            |       -        |
  | top           | String        |    是         | 0取消置顶 1置顶 |      -     |       -         |
  | publishDate   | Date          |    是         | 发布时间       | -             |     -        |
  | updateToporNodate | Date      |    是         | 更新置顶状态时间       | -      |      -       |
  | expireDate    | Date          |    是         | 过期时间       | -             |     -        |
  | type          | Json          |    是         | 公告类型Json对象 | -            |     -       |

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

  参数：type 为新闻公告类型的json, 创建新闻公告详情时异步请求获取其对象具体uri 参考新闻公告类型接口文档。

### 置顶或取消置顶(兼容批量)

- **请求uri**

  bulletinInfo/updateToporNo

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | id            | String        |    是         | 新闻公告id     | -             |      101      |
  | top           | String        |    是         | 0取消置顶 1置顶 |      -     |       -         |

  **返回正确JSON示例**
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

    支持批量处理，后端接收Json数组

### 删除新闻公告详情(兼容批量删除)

- **请求uri**

  bulletinInfo/delete

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | ids           | String        |    是         | 新闻公告ids     | -             |      101      |

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

  bulletinInfo/getListPageByCondition/{eid}

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/application/json"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id       | -             |      101      |
  | pageNumber    | int           |    是         | 页码           | -             |     -         |
  | pageSize      | String        |    是         | 页面大小       | -             |       -       |
  | title         | String        |    是         | 标题          | -             |       -       |
  | bulletinType  | String        |    是         | 公告类型       | -            |     -         |
  | status        | String        |    是         | 0为草稿 1为发布| -            |       -        |

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
### 获取所有新闻公告详情

- **请求uri**

  bulletinInfo/getListByPage/{eid}?pageNumber=0&pageSize=20

- **请求方式**

  get

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id       | -             |      101      |
  | pageNumber    | int           |    是         | 页码           | -             |     -         |
  | pageSize      | String        |    是         | 页面大小       | -             |       -       |

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
### 懒惰加载最新新闻公告详情

- **请求uri**

  bulletinInfo/app/getLatest

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101      |
  | publishDate   | Date          |    是         | 发布时间       | -             |     -        |

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
### 懒惰加载某类新闻公告详情

- **请求uri**

  bulletinInfo/app/type/getLatest

- **请求方式**

  post

- **请求头**

  "key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"

- **请求参数**

  | 参数名称       | 类型          | 必填          | 描述           | 默认值        | 参考值         |
  | ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -------------:|
  | eid           | String        |    是         | 工作圈id      | -             |      101      |
  | bulletinType  | String        |    是         | 公告类型       | -            |     -         |
  | publishDate   | Date          |    是         | 发布时间       | -             |     -        |

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
