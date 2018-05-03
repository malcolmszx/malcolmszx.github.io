---
layout:     post
title:      管理员
subtitle:   CURD
date:       2017-05-03
author:     BY Malcolmszx
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - interface
---

### 创建新闻公告管理员

1. **请求uri**<br>
bulletinAdmin/create
2. **请求方式**<br>
post
3. **请求头**<br>
"key" : "Content-Type",  "value" : "application/json"
4. **请求参数**
     <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td> -  </td> <td>101</td>
        </tr>
        <tr>
        <td>pubId</td> <td>String</td> <td>是</td> <td>公共号ID</td> <td> -  </td> <td>XT-717062e8-8ee5-4873-a607-e8ccf4e8068f</td>
        </tr>
        <tr>
            <td>id</td> <td>String</td> <td> 否</td> <td>管理员ID</td> <td> -  </td> <td>-</td>
        </tr>
         <tr>
            <td>name</td> <td>String</td> <td>是</td> <td>名称</td> <td> -  </td> <td>-</td>
        </tr>
         <tr>
            <td>oid</td> <td>String</td> <td>是</td> <td>用户oid</td> <td> -  </td> <td>-</td>
        </tr>
         <tr>
            <td>status</td> <td>String</td> <td>是</td> <td>0为删除 1为正常</td> <td> - </td> <td>1</td>
        </tr>
        <tr>
            <td>creatorName</td> <td>String</td> <td>是</td> <td>创建人名称</td> <td> -  </td> <td>-</td>
        </tr>
        <tr>
            <td>creatorOId</td> <td>String</td> <td>是</td> <td>创建人oID</td> <td> -  </td> <td>-</td>
         </tr>
         <tr>
            <td>creatorDate</td> <td>Date</td> <td>是</td> <td>创建日期</td> <td> -  </td><td>1525230414</td>
         </tr>
    </table> 
5. **返回正确JSON示例**<br>
    {<br>
        &emsp;"code": 200,<br>
        &emsp;"msg": "请求成功",<br>
        &emsp;"data": null<br> 
    }<br>
6. **返回错误JSON示例**<br>
    {<br>
       &emsp; "code": 201,<br>
       &emsp; "msg": "请求失败"<br>
    }<br>
7. **备注**<br>
     兼容添加多个新闻公告管理员,后端接收json数组：[{{"eid":"236","pubId":"XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",...},{...}]
     
### 获取新闻公告管理员列表

- **请求uri**<br>
bulletinAdmin/list
- **请求方式**<br>
post
- **请求头**<br>
"key" : "Content-Type",  "value" : "x-www-form-urlencoded"<br>
- **请求参数**
    <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td> -  </td> <td>236</td>
        </tr>
        <tr>
            <td>pubId</td> <td>String</td> <td>是</td> <td>公共号ID</td> <td> -  </td> <td>XT-717062e8-8ee5-4873-a607-e8ccf4e8068f</td>
        </tr>
        <tr>
            <td>status</td> <td>String</td> <td>是</td> <td>0为删除 1为正常</td> <td> - </td> <td>1</td>
        </tr>
    </table> 
- **返回正确JSON示例**<br>
    {<br>
     &emsp;"code": 200,<br>
     &emsp;"msg": "请求成功",<br>
     &emsp;"data": [<br>
          &emsp;&emsp;&emsp;&emsp;{<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"eid": "236",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "pubId": "XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "id": "5aea747329bbf602349dcf5d",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "oid": "5ae92a4f29bbf603904abce9",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "name": "黄小明",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "creatorOId": "5ae92a4f29bbf603904abcf5",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "creatorName": "张航",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "creatorDate": 1525229096,<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "status": "1"<br>
        &emsp;&emsp;&emsp;&emsp;},<br>
        &emsp;&emsp;&emsp;&emsp;{<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "eid": "236",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "pubId": "XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "id": "5aea747329bbf602349dcf5e",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "oid": "5be82a4f29bbf603904abce9",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "name": "李贵",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "creatorOId": "5ae92a4f29bbf603904abcf5",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "creatorName": "张航",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "creatorDate": 1625228096,<br>
            &emsp;&emsp;&emsp;&emsp;&emsp; "status": "1"<br>
         &emsp;&emsp;&emsp;&emsp;}<br>
     &emsp;&emsp;&emsp;]<br>
}<br>
- **返回错误JSON示例**<br>
    {<br>
       &emsp; "code": 201,<br>
       &emsp; "msg": "请求失败"<br>
    }<br>
    
### 删除新闻公告管理员

- **请求uri** <br>
bulletinAdmin/delete
- **请求方式** <br>
post
- **请求头** <br>
"key" : "Content-Type",  "value" : "x-www-form-urlencoded"<br>
- **请求参数**
    <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td> -  </td> <td>236</td>
        </tr>
        <tr>
            <td>pubId</td> <td>String</td> <td>是</td> <td>公共号ID</td> <td> -  </td> <td>XT-717062e8-8ee5-4873-a607-e8ccf4e8068f</td>
        </tr>
        <tr>
            <td>status</td> <td>String</td> <td>是</td> <td>0为删除 1为正常</td> <td> - </td> <td>1</td>
        </tr>
        <tr>
            <td>ids</td> <td>List<String></td> <td>是</td> <td>管理员编号id</td> <td> -  </td> <td>5ae92a4f29bbf603904abcf5</td>
        </tr>
    </table> 
 - **返回正确JSON示例**<br>
    {<br>
        &emsp;"code": 200,<br>
        &emsp;"msg": "请求成功",<br>
        &emsp;"data": null<br> 
    }<br>
- **返回错误JSON示例**<br>
    {<br>
       &emsp; "code": 201,<br>
       &emsp; "msg": "请求失败"<br>
    }<br>
    
### 查询新闻公告管理员

- **请求uri**<br>
bulletinAdmin/query
- **请求方式**<br>
post
- **请求头**<br>
"key" : "Content-Type",  "value" : "x-www-form-urlencoded"<br>
- **请求参数**


 | 参数名称 | 类型 | 必填 | 描述 | 默认值 | 参考值 |
 | :--  | :--: | ----: | :--  | :--: | ----: |
 | eid | String | 是 | 工作圈ID | - | 236 |
 | pubId | String | 是 | 公共号ID | - | XT-717062e8-8ee5-4873-a607-e8ccf4e8068f |
 | status | String | 是 | 0为删除 1为正常 | - | 1 |
 | name | String | 是 | 名称 | - | 黄 |


- **返回正确JSON示例**<br>    
{<br>
     &emsp;"code": 200,<br>
     &emsp;"msg": "请求成功",<br>
     &emsp;"data": [<br>
        &emsp;&emsp;&emsp;{<br>
            &emsp;&emsp;&emsp;&emsp;"eid": "236",<br>
            &emsp;&emsp;&emsp;&emsp;"pubId": "XT-717062e8-8ee5-4873-a607-e8ccf4e8068f",<br>
            &emsp;&emsp;&emsp;&emsp;"id": "5aea747329bbf602349dcf5d",<br>
            &emsp;&emsp;&emsp;&emsp;"oid": "5ae92a4f29bbf603904abce9",<br>
            &emsp;&emsp;&emsp;&emsp;"name": "黄小明",<br>
            &emsp;&emsp;&emsp;&emsp;"creatorOId": "5ae92a4f29bbf603904abcf5",<br>
            &emsp;&emsp;&emsp;&emsp;"creatorName": "张航",<br>
            &emsp;&emsp;&emsp;&emsp;"creatorDate": 1525229960,<br>
           &emsp;&emsp;&emsp;&emsp; "status": "0"<br>
        &emsp;&emsp;&emsp;}<br>
    &emsp;]<br>
}<br>
