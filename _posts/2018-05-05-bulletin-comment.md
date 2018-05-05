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

1. **请求uri**<br>
bulletinComment/save
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
            <td>bullentinId</td> <td>String</td> <td>是</td> <td>新闻公告id</td> <td> - </td> <td>-</td>
        </tr>
        <tr>
            <td>content</td> <td>String</td> <td>是</td> <td>评论内容</td> <td> -  </td> <td>0</td>
        </tr>
         <tr>
            <td>createTime</td> <td>String</td> <td>是</td> <td>评论时间</td> <td> -  </td><td>-</td>
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
    
### 点赞/取消新闻公告评论

1. **请求uri**<br>
bulletinComment/updateParise
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
            <td>comment</td> <td>String</td> <td>是</td> <td>评论id</td> <td> -  </td> <td>0</td>
        </tr>
         <tr>
            <td>addOrdelete</td> <td>String</td> <td>是</td> <td>true 添加 false 取消</td> <td> -  </td><td>-</td>
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
    
