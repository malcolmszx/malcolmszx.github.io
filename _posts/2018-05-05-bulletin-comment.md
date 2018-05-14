---
layout:     post
title: 新闻公告留言
subtitle: editor and so on
date:       2018-05-05
author:     BY Malcolmszx
header-img: img/post-bg-debug.png
catalog: true
tags:
    - interface
---
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
  ````   
- **返回错误JSON示例**
  ```
    {
        "code": 205,
        "msg": "参数不正确"
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
