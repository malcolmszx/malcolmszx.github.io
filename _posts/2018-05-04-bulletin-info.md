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
     <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>ids</td> <td>List</td> <td>是</td> <td>新闻公告ids</td> <td> -  </td> <td>-</td>
        </tr>
    </table>
- **返回正确JSON示例**
    {
        &emsp;"code": 200,
        &emsp;"msg": "请求成功",
        &emsp;"data": null
    }
- **返回错误JSON示例**
    {
       &emsp; "code": 201,
       &emsp; "msg": "请求失败"
    }

### 条件查询新闻公告详情

- **请求uri**
bulletinInfo/getListPageByCondition/{eid}
- **请求方式**
post
- **请求头**
"key" : "Content-Type",  "value" : "application/application/json"
- **请求参数**
     <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td> -  </td> <td>101</td>
        </tr>
        <tr>
            <td>pageNumber</td> <td>int</td> <td>是</td> <td>页面</td> <td> -  </td> <td>-</td>
        </tr>
        <tr>
            <td>pageSize</td> <td>int</td> <td>是</td> <td>页面大小</td> <td> 20 </td> <td>20</td>
        </tr>
        <tr>
            <td>title</td> <td>String</td> <td>否</td> <td>标题</td> <td> -  </td> <td>-</td>
        </tr>
        <tr>
            <td>bulletinType</td> <td>String</td> <td>否</td> <td>公告类型</td> <td> -  </td> <td>员工发展</td>
        </tr>
        <tr>
            <td>status</td> <td>String</td> <td>是</td> <td> 0为草稿 1为发布 </td> <td> - </td> <td>1</td>
        </tr>
    </table>
- **返回正确JSON示例**
{
    &emsp;"code":200,
    &emsp;"msg":"请求成功",
    &emsp;"data":{
        &emsp;&emsp;&emsp;"content":[
           &emsp;&emsp;&emsp;&emsp;{
                 &emsp;&emsp;&emsp;&emsp;&emsp;"id":"5aebc35329bbf612bc09bc6b",
                 &emsp;&emsp;&emsp;&emsp;&emsp;"title":"百度资讯发送消息",
                 &emsp;&emsp;&emsp;&emsp;&emsp;"subTitle":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"author":"5ad5c3ec29bbf624b4784628",
                 &emsp;&emsp;&emsp;&emsp;&emsp;"status":"1",
                 &emsp;&emsp;&emsp;&emsp;&emsp;"expireDate":1525399807,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"url":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"content":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"pic":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"articleUrl":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"articleId":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"attachments":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp; "type":{
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"id":"9ad5c3ec29bbf624b4784628",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"name":"员工发展",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"insideShare":"1",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"outsideShare":"0",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"comment":null,
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"status":"1",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"seq":null,
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"delete":"1",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"creator":null,
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"creatorDate":null,
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"eid":"236"
                &emsp;&emsp;&emsp;&emsp;},
                &emsp;&emsp;&emsp;&emsp;&emsp;"readnum":0,
                &emsp;&emsp;&emsp;&emsp;&emsp;"praisenum":0,
                &emsp;&emsp;&emsp;&emsp;&emsp;"creator":null,
                &emsp;&emsp;&emsp;&emsp;&emsp;"publishDate":1525399857,
                &emsp;&emsp;&emsp;&emsp;&emsp;"eid":"236",
                &emsp;&emsp;&emsp;&emsp;&emsp;"delete":"1",
                &emsp;&emsp;&emsp;&emsp;&emsp;"top":"0",
                &emsp;&emsp;&emsp;&emsp;&emsp;"orderType":"2",
                &emsp;&emsp;&emsp;&emsp;&emsp;"bulletinType":"员工发展",
                &emsp;&emsp;&emsp;&emsp;&emsp;"updateToporNodate":1525399957,
                &emsp;&emsp;&emsp;&emsp;&emsp;"bulletinMsgtype":"6"
             &emsp;&emsp;&emsp;&emsp;}
         &emsp;&emsp;&emsp;],
        "totalPages":1,
        "totalElements":1,
        "last":true,
        "number":0,
        "size":20,
        "sort":[
         &emsp;&emsp;{
                &emsp;&emsp;&emsp;&emsp;"direction":"DESC",
                &emsp;&emsp;&emsp;&emsp;"property":"publishDate",
                &emsp;&emsp;&emsp;&emsp;"ignoreCase":false,
                &emsp;&emsp;&emsp;&emsp;"nullHandling":"NATIVE",
                &emsp;&emsp;&emsp;&emsp;"ascending":false,
                &emsp;&emsp;&emsp;&emsp;"descending":true
          &emsp;&emsp;}
         &emsp;],
        "numberOfElements":1,
        "first":true
     &emsp;}
}

### 获取所有新闻公告详情

- **请求uri**
bulletinInfo/getListByPage/{eid}?pageNumber=0&pageSize=20
- **请求方式**
get
- **请求头**
- **请求参数**
     <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td> -  </td> <td>101</td>
        </tr>
        <tr>
            <td>pageNumber</td> <td>int</td> <td>是</td> <td>页面</td> <td> -  </td> <td>-</td>
        </tr>
        <tr>
            <td>pageSize</td> <td>int</td> <td>是</td> <td>页面大小</td> <td> 20 </td> <td>20</td>
        </tr>
    </table>
- **返回正确JSON示例**
{
    &emsp;"code":200,
    &emsp;"msg":"请求成功",
    &emsp;"data":{
        &emsp;&emsp;&emsp;"content":[
           &emsp;&emsp;&emsp;&emsp;{
                 &emsp;&emsp;&emsp;&emsp;&emsp;"id":"5aebc35329bbf612bc09bc6b",
                 &emsp;&emsp;&emsp;&emsp;&emsp;"title":"百度资讯发送消息",
                 &emsp;&emsp;&emsp;&emsp;&emsp;"subTitle":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"author":"5ad5c3ec29bbf624b4784628",
                 &emsp;&emsp;&emsp;&emsp;&emsp;"status":"1",
                 &emsp;&emsp;&emsp;&emsp;&emsp;"expireDate":1525399807,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"url":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"content":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"pic":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"articleUrl":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"articleId":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"attachments":null,
                 &emsp;&emsp;&emsp;&emsp;&emsp;"type":
                 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;{
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"id":"9ad5c3ec29bbf624b4784628",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"name":"员工发展",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"insideShare":"1",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"outsideShare":"0",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"comment":null,
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"status":"1",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"seq":null,
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"delete":"1",
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"creator":null,
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"creatorDate":null,
                    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"eid":"236"
                &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;},
                &emsp;&emsp;&emsp;&emsp;&emsp;"readnum":0,
                &emsp;&emsp;&emsp;&emsp;&emsp;"praisenum":0,
                &emsp;&emsp;&emsp;&emsp;&emsp;"creator":null,
                &emsp;&emsp;&emsp;&emsp;&emsp;"publishDate":1525399857,
                &emsp;&emsp;&emsp;&emsp;&emsp;"eid":"236",
                &emsp;&emsp;&emsp;&emsp;&emsp;"delete":"1",
                &emsp;&emsp;&emsp;&emsp;&emsp;"top":"0",
                &emsp;&emsp;&emsp;&emsp;&emsp;"orderType":"2",
                &emsp;&emsp;&emsp;&emsp;&emsp;"bulletinType":"员工发展",
                &emsp;&emsp;&emsp;&emsp;&emsp;"updateToporNodate":1525399957,
                &emsp;&emsp;&emsp;&emsp;&emsp;"bulletinMsgtype":"6"
             &emsp;&emsp;&emsp;&emsp;}
         &emsp;&emsp;&emsp;],
        "totalPages":1,
        "totalElements":1,
        "last":true,
        "number":0,
        "size":20,
        "sort":[
         &emsp;&emsp;{
                &emsp;&emsp;&emsp;&emsp;"direction":"DESC",
                &emsp;&emsp;&emsp;&emsp;"property":"publishDate",
                &emsp;&emsp;&emsp;&emsp;"ignoreCase":false,
                &emsp;&emsp;&emsp;&emsp;"nullHandling":"NATIVE",
                &emsp;&emsp;&emsp;&emsp;"ascending":false,
                &emsp;&emsp;&emsp;&emsp;"descending":true
          &emsp;&emsp;}
         &emsp;],
        "numberOfElements":1,
        "first":true
     &emsp;}
}

### 懒惰加载最新新闻公告详情

- **请求uri**
bulletinInfo/app/getLatest
- **请求方式**
post
- **请求头**
"key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"
- **请求参数**
     <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td> -  </td> <td>236</td>
        </tr>
       <tr>
            <td>publishDate</td> <td>Date</td> <td>是</td> <td>发布时间</td> <td> -  </td> <td>2018/5/4 10:10:57</td>
       </tr>
    </table>
 - **返回正确JSON示例**
 {
     &emsp;"code": 200,
     &emsp;"msg": "请求成功",
     &emsp;"data": [
         &emsp;&emsp;&emsp;{
            &emsp;&emsp;&emsp;&emsp;"id": "5aebc35329bbf612bc09bc6b",
            &emsp;&emsp;&emsp;&emsp; "title": "百度资讯发送消息",
            &emsp;&emsp;&emsp;&emsp; "subTitle": null,
            &emsp;&emsp;&emsp;&emsp; "author": "5ad5c3ec29bbf624b4784628",
            &emsp;&emsp;&emsp;&emsp; "status": "1",
            &emsp;&emsp;&emsp;&emsp;"expireDate": 1525399807,
            &emsp;&emsp;&emsp;&emsp; "url": null,
            &emsp;&emsp;&emsp;&emsp; "content": null,
            &emsp;&emsp;&emsp;&emsp; "pic": null,
            &emsp;&emsp;&emsp;&emsp;"articleUrl": null,
            &emsp;&emsp;&emsp;&emsp; "articleId": null,
            &emsp;&emsp;&emsp;&emsp;"attachments": null,
            &emsp;&emsp;&emsp;&emsp;"type":
            &emsp;&emsp;&emsp;&emsp;&emsp;{
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"id": "9ad5c3ec29bbf624b4784628",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"name": "员工发展",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"insideShare": "1",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"outsideShare": "0",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"comment": null,
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"status": "1",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"seq": null,
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"delete": "1",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"creator": null,
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"creatorDate": null,
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"eid": "236"
            &emsp;&emsp;&emsp;&emsp;&emsp;},
            &emsp;&emsp;&emsp;&emsp;"readnum": 0,
            &emsp;&emsp;&emsp;&emsp;"praisenum": 0,
            &emsp;&emsp;&emsp;&emsp;"creator": null,
            &emsp;&emsp;&emsp;&emsp;"publishDate": 1525399857,
            &emsp;&emsp;&emsp;&emsp;"eid": "236",
            &emsp;&emsp;&emsp;&emsp;"delete": "1",
            &emsp;&emsp;&emsp;&emsp;"top": "0",
            &emsp;&emsp;&emsp;&emsp;"orderType": "2",
            &emsp;&emsp;&emsp;&emsp;"bulletinType": "员工发展",
            &emsp;&emsp;&emsp;&emsp;"updateToporNodate": 1525399957,
            &emsp;&emsp;&emsp;&emsp;"bulletinMsgtype": "6"
        &emsp;&emsp;&emsp;}
    &emsp;&emsp;&emsp;&emsp;]
}

### 懒惰加载某类新闻公告详情

- **请求uri**
bulletinInfo/app/type/getLatest
- **请求方式**
post
- **请求头**
"key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"
- **请求参数**
     <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td> -  </td> <td>236</td>
        </tr>
        <tr>
            <td>bulletinType</td> <td>String</td> <td>是</td> <td>新闻公告类型</td> <td> -  </td> <td>员工发展</td>
        </tr>
       <tr>
            <td>publishDate</td> <td>Date</td> <td>是</td> <td>发布时间</td> <td> -  </td> <td>2018/5/4 10:10:57</td>
       </tr>
    </table>
 - **返回正确JSON示例**
 {
     &emsp;"code": 200,
     &emsp;"msg": "请求成功",
     &emsp;"data": [
         &emsp;&emsp;&emsp;{
            &emsp;&emsp;&emsp;&emsp;"id": "5aebc35329bbf612bc09bc6b",
            &emsp;&emsp;&emsp;&emsp; "title": "百度资讯发送消息",
            &emsp;&emsp;&emsp;&emsp; "subTitle": null,
            &emsp;&emsp;&emsp;&emsp; "author": "5ad5c3ec29bbf624b4784628",
            &emsp;&emsp;&emsp;&emsp; "status": "1",
            &emsp;&emsp;&emsp;&emsp;"expireDate": 1525399807,
            &emsp;&emsp;&emsp;&emsp; "url": null,
            &emsp;&emsp;&emsp;&emsp; "content": null,
            &emsp;&emsp;&emsp;&emsp; "pic": null,
            &emsp;&emsp;&emsp;&emsp;"articleUrl": null,
            &emsp;&emsp;&emsp;&emsp; "articleId": null,
            &emsp;&emsp;&emsp;&emsp;"attachments": null,
            &emsp;&emsp;&emsp;&emsp;"type":
            &emsp;&emsp;&emsp;&emsp;&emsp;{
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"id": "9ad5c3ec29bbf624b4784628",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"name": "员工发展",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"insideShare": "1",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"outsideShare": "0",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"comment": null,
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"status": "1",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"seq": null,
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"delete": "1",
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"creator": null,
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"creatorDate": null,
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;"eid": "236"
            &emsp;&emsp;&emsp;&emsp;&emsp;},
            &emsp;&emsp;&emsp;&emsp;"readnum": 0,
            &emsp;&emsp;&emsp;&emsp;"praisenum": 0,
            &emsp;&emsp;&emsp;&emsp;"creator": null,
            &emsp;&emsp;&emsp;&emsp;"publishDate": 1525399857,
            &emsp;&emsp;&emsp;&emsp;"eid": "236",
            &emsp;&emsp;&emsp;&emsp;"delete": "1",
            &emsp;&emsp;&emsp;&emsp;"top": "0",
            &emsp;&emsp;&emsp;&emsp;"orderType": "2",
            &emsp;&emsp;&emsp;&emsp;"bulletinType": "员工发展",
            &emsp;&emsp;&emsp;&emsp;"updateToporNodate": 1525399957,
            &emsp;&emsp;&emsp;&emsp;"bulletinMsgtype": "6"
        &emsp;&emsp;&emsp;}
    &emsp;&emsp;&emsp;&emsp;]
}
