---
title: Postman进阶篇
categories: 测试
tags: Postman
date: 2017-12-11
---
Postman设置变量

<!-- more -->


## 一、变量
**设置全局变量和环境变量**
例如：我们的项目有3个环境分别是测试环境、预发布、和线上，它们的domain都是 XXX.chime.me.
测试环境：test.chime.me
预发布：prerelease.chime.me
线上：chime.me
为了不用每个环境都去写一遍接口，我们可以把XXX设置成为环境变量，测试不同的环境，只需要切换环境变量即可。

** 如何在postman中设置环境变量：**
1、把HTTP中XXX.设置为变量“domain_name”，即

 	http://{{domain_name}}chime.me/
 
2、点击右上的小眼睛，添加3环境个变量
![](/bimg/11.jpg)
![](/bimg/12.jpg)

3、选择对应的环境，变量填充成对应的值：
![](/bimg/13.jpg)


## 二、运行collection
![](/bimg/14.jpg)

## 三、从命令行运行postman脚本
运行准备：
导出collection
安装nodejs和npm
安装newman

### 1、导出collection:
![](/bimg/15.jpg)
点击Export即可导出一个JSON格式的文件。

### 2、安装nodejs和npm
下载安装nodejs
http://nodejs.cn/download/

### 3、安装newman
运行命令行 ：

	$ npm install newman --global;

![](/bimg/16.png)

### 运行postman脚本
安装成功后使用newman运行导出的JSON文件

	$ newman run XXX.json -d data.json -r 生成的报告格式

-d ：添加测试数据变量
-r ：生成报告的格式，可生成多种格式的报告

