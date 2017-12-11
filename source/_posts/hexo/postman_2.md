---
title: Postman设置变量
categories: 测试
tags: Postman
date: 2017-12-11
---
Postman设置变量

<!-- more -->

## 九、postman的sandbox

## 十、使用postman设置请求方法

## 十一、postman与cookie

## 十二、鉴权

## 十三、collection

## 十四、变量
设置全局变量和环境变量
例如：我们的项目有3个环境分别是测试环境、预发布、和线上，它们的domain都是 XXX.chime.me.
测试环境：test.chime.me
预发布：prerelease.chime.me
线上：chime.me
为了不用每个环境都去写一遍接口，我们可以把XXX设置成为环境变量，测试不同的环境，只需要切换环境变量即可。
** 如何在postman中设置环境变量：**
1、把HTTP中XXX设置为变量“domain_name”，即 http://{{domain_name}}chime.me/
2、点击右上的小眼睛，添加3环境个变量
![](/bimg/11.jpg)
![](/bimg/12.jpg)

3、选择对应的环境，变量填充成对应的值：
![](/bimg/13.jpg)


## 十五、运行collection
![](/bimg/14.jpg)

## 十六、从命令行运行postman脚本

## 十七、导出Python脚本进行数据驱动