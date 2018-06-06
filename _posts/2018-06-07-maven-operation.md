---
layout:     post
title:  maven 项目管理
subtitle:  常用命令
date:       2018-06-07
author:     BY Malcolmszx@gmail.com
header-img: img/post-bg-mma-5.jpg
catalog: true
tags:
    - 终端
    - maven
---

# maven 常用命令

- mvn -version         查看maven的版本及配置信息

- mvn archetype:create   -DgroupId=    DartifactId=    构建java项目

- mvn archetype:create   -DgroupId=    DartifactId=    -DarchetypeArtifactId=maven-archetype-webapp 创建web项目

- mvn compile         编译项目代码

- mvn package         打包项目

- mvn package -Dmaven.test.skip=true   打包项目时跳过单元测试

- mvn test            运行单元测试

- mvn clean           清除编译产生的target文件夹内容，可以配合相应命令一起使用，如mvn clean package， mvn clean test

- mvn install         打包后将其安装在本地仓库

- mvn deploy          打包后将其安装到pom文件中配置的远程仓库

- mvn eclipse:eclipse       将maven生成eclipse项目结构

- mvn eclipse:clean         清除maven项目中eclipse的项目结构

- mvn site                  生成站点目录

- mvn dependency:list       显示所有已经解析的所有依赖

- mvn dependency:tree       以树的结构展示项目中的依赖

- mvn dependency:analyze    对项目中的依赖进行分析，依赖未使用，使用单未引入

- mvn tomcat:run            启动tomcat