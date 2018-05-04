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

1. **请求uri**<br>
bulletinInfo/save
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
            <td>author</td> <td>String</td> <td>是</td> <td> 创建人的 oId </td> <td> -  </td> <td>-</td>
        </tr>
        <tr>
            <td>title</td> <td>String</td> <td> 是</td> <td>标题</td> <td> -  </td> <td>-</td>
        </tr>
        <tr>
            <td>bulletinMsgtype</td> <td>String</td> <td>是</td> <td> 公告内容类型 </td> <td> 单图文  </td> <td>6</td>
        </tr>
        <tr>
            <td>bulletinType</td> <td>String</td> <td>是</td> <td>公告类型</td> <td> -  </td> <td>员工发展</td>
        </tr>
         <tr>
            <td>orderType</td> <td>String</td> <td>是</td> <td>显示顺序</td> <td> -  </td> <td>-</td>
        </tr>
         <tr>
            <td>status</td> <td>String</td> <td>是</td> <td> 0为草稿 1为发布 </td> <td> - </td> <td>1</td>
        </tr>
        <tr>
            <td>top</td> <td>String</td> <td>是</td> <td> 0取消置顶 1置顶 </td> <td> -  </td> <td>0</td>
        </tr>
        <tr>
            <td>publishDate</td> <td>Date</td> <td>是</td> <td> 发布时间 </td> <td> -  </td> <td>1525399857</td>
         </tr>
         <tr>
            <td>updateToporNodate</td> <td>Date</td> <td>是</td> <td> 更新置顶状态时间 </td> <td> -  </td><td>1525399957</td>
         </tr>
          <tr>
            <td>expireDate</td> <td>Date</td> <td>是</td> <td> 过去时间 </td> <td> -  </td><td>1525399957</td>
         </tr>
         <tr>
            <td>type</td> <td>Json</td> <td>是</td> <td> 公告类型Json对象 </td> <td> -  </td><td>-</td>
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
     参数：type 为新闻公告类型的json, 创建新闻公告详情时异步请求获取其对象具体uri 参考新闻公告类型接口文档
     
### 删除新闻公告详情(兼容批量删除)

- **请求uri**<br>
bulletinInfo/delete
- **请求方式**<br>
post
- **请求头**<br>
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
