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
  | col 3 is      | right-aligned |    $1600      | col 3 is      | right-aligned |     $1600     |
  | col 2 is      | centered      |   col 2 is    | centered      | col 4 is      | centered      |
  | zebra stripes | are neat      |   col 5 is    | centered      |       -       |      -        |    

- **请求参数**

    <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>id</td> <td>String</td> <td> 否</td> <td>新闻公告类型ID</td> <td>  -   </td> <td>-</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td>  -   </td> <td>101</td>
        </tr>
         <tr>
            <td>name</td> <td>String</td> <td>是</td> <td>类型</td> <td>  -   </td> <td>员工发展</td>
        </tr>
          <tr>
            <td>seq</td> <td>String</td> <td>是</td> <td>显示顺序</td> <td>  -   </td> <td>1</td>
        </tr>
         <tr>
            <td>status</td> <td>String</td> <td>是</td> <td>0为禁用 1为启用</td> <td>  1 </td> <td>1</td>
        </tr>
          <tr>
            <td>insideShare</td> <td>String</td> <td>是</td> <td>内部分享 0为不允许 1为允许</td> <td>  -   </td> <td>1</td>
        </tr>
         <tr>
            <td>outsideShare</td> <td>String</td> <td>是</td> <td>外部分享  0为不允许  1为允许</td> <td>  -   </td> <td>0</td>
        </tr>
          <tr>
            <td>comment</td> <td>String</td> <td>是</td> <td>评论  0为不允许  1为允许</td> <td>  -   </td> <td>1</td>
        </tr>
         <tr>
            <td>creator</td> <td>String</td> <td>是</td> <td>创建人ID</td> <td>  -   </td> <td></td>
        </tr>
          <tr>
            <td>creatorDate</td> <td>Date</td> <td>是</td> <td>创建日期</td> <td>  -   </td><td>1525230414</td>
        </tr>
         <tr>
            <td>delete</td> <td>String</td> <td>是</td> <td>删除   0为已删除 1为正常</td> <td>  1 </td> <td>1</td>
        </tr>
    </table>

- **返回正确JSON示例**

  {
    "code": 200,
    "msg": "请求成功",
    "data": null
  }

7. **返回错误JSON示例**

  {
     "code": 201,
     "msg": "请求失败"
  }

8. **请求成功，但是创建失败**

  {
      "code": 202,
      "msg": "该类型存在"
  }

9. **备注**

  当创建的新闻公告类型已经存在时，创建失败，返回状态码code：202 msg:该类型存在

### 编辑新闻公告类型

1. **请求uri**<br>
/bulletinType/editor
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
            <td>id</td> <td>String</td> <td>是</td> <td>新闻公告类型ID</td> <td>  -   </td> <td>5ae92a4f29bbf603104abce9</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td>  -   </td> <td>101</td>
        </tr>
         <tr>
            <td>name</td> <td>String</td> <td>是</td> <td>类型</td> <td>  -   </td> <td>员工发展</td>
        </tr>
          <tr>
            <td>seq</td> <td>String</td> <td>是</td> <td>显示顺序</td> <td>  -   </td> <td>1</td>
        </tr>
         <tr>
            <td>status</td> <td>String</td> <td>是</td> <td>0为禁用 1为启用</td> <td>  1 </td> <td>1</td>
        </tr>
          <tr>
            <td>insideShare</td> <td>String</td> <td>是</td> <td>内部分享 0为不允许 1为允许</td> <td>  -   </td> <td>1</td>
        </tr>
         <tr>
            <td>outsideShare</td> <td>String</td> <td>是</td> <td>外部分享  0为不允许  1为允许</td> <td>  -   </td> <td>0</td>
        </tr>
          <tr>
            <td>comment</td> <td>String</td> <td>是</td> <td>评论  0为不允许  1为允许</td> <td>  -   </td> <td>1</td>
        </tr>
         <tr>
            <td>creator</td> <td>String</td> <td>是</td> <td>创建人ID</td> <td>  -   </td> <td></td>
        </tr>
          <tr>
            <td>creatorDate</td> <td>Date</td> <td>是</td> <td>创建日期</td> <td>  -   </td><td>1525230414</td>
        </tr>
         <tr>
            <td>delete</td> <td>String</td> <td>是</td> <td>删除   0为已删除 1为正常</td> <td>  1 </td> <td>1</td>
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

### 获取新闻公告类型列表

1. **请求uri**<br>
/bulletinType/getList
2. **请求方式**<br>
get <br>
如：http://localhost:8099/bulletin/bulletinType/getList/236/1<br>
3. **请求参数**
    <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td>  -   </td> <td>101</td>
        </tr>
        <tr>
            <td>delete</td> <td>String</td> <td> 是 </td> <td>删除状态</td> <td>  -   </td> <td>1</td>
        </tr>
    </table>
4. **返回正确JSON示例**<br>
{<br>
    &emsp;"code":200,<br>
    &emsp;"msg":"请求成功",<br>
    &emsp;"data":[<br>
        &emsp;&emsp;&emsp;&emsp;{<br>
            &emsp;&emsp; &emsp;&emsp;&emsp;"id":"5ae92a4f29bbf603104abce9",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"name":"员工发展",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"insideShare":"1",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"outsideShare":"0",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"comment":"0",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"status":"1",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"seq":"2",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"delete":"1",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"creator":"5ae92a4f29bbf603904abce9",<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"creatorDate":1525229096,<br>
            &emsp;&emsp;&emsp;&emsp;&emsp;"eid":"236"<br>
       &emsp;&emsp;&emsp;&emsp;}<br>
    &emsp;&emsp;&emsp;]<br>
}<br>

### 删除新闻公告类型
1. **请求uri**<br>
/bulletinType/delete
2. **请求方式**<br>
post
3. **请求头**<br>
"key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"
4. **请求参数**
    <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
         <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td>  -   </td> <td>236</td>
        </tr>
        <tr>
            <td>id</td> <td>String</td> <td> 是 </td> <td>新闻公告类型ID</td> <td>  -   </td> <td></td>
        </tr>
         <tr>
            <td>name</td> <td>String</td> <td>是</td> <td>名称</td> <td>  -   </td> <td>人员发展</td>
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
7. **请求成功，但是删除失败**<br>
  {<br>
       &emsp; "code": 202,<br>
       &emsp; "msg": "该分类下有新闻公告内容，暂不可删除，如需删除，请先移走该分类下的内容"<br>
       &emsp; "data": null<br>
    }<br>

### 更新新闻公告类型状态
1. **请求uri**<br>
/bulletinType/updateStatus
2. **请求方式**<br>
post
3. **请求头**<br>
"key" : "Content-Type",  "value" : "application/x-www-form-urlencoded"
4. **请求参数**
    <table>
        <tr>
            <td>参数名称</td> <td>类型</td> <td>必填</td> <td>描述</td> <td>默认值</td> <td>参考值</td>
        </tr>
        <tr>
            <td>eid</td> <td>String</td> <td>是</td> <td>工作圈ID</td> <td>  -   </td> <td>236</td>
        </tr>
        <tr>
            <td>id</td> <td>String</td> <td> 是 </td> <td>新闻公告类型ID</td> <td>  -   </td> <td></td>
        </tr>
         <tr>
            <td>status</td> <td>String</td> <td>是</td> <td>0为禁用 1为启用</td> <td>  1 </td> <td>1</td>
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
