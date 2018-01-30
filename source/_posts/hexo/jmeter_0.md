---
title: Jmeter接口测试入门
categories: 测试
tags: Jmeter
date: 2018-1-26
---
Jmeter介绍以及安装
<!-- more -->

## Jmeter简介
jmeter是apache公司基于java开发的一款开源压力测试工具，体积小，功能全，使用方便，是一个比较轻量级的测试工具，使用起来非常简单。因为jmeter是java开发的，所以运行的时候必须先要安装jdk才可以。jmeter是免安装的，拿到安装包之后直接解压就可以使用，同时它在linux/windows/macos上都可以使用。 

jmeter可以做接口测试和压力测试。其中接口测试的简单操作包括做http脚本（发get/post请求、加cookie、加header、加权限认证、上传文件）、做webservice脚本、参数化、断言、关联（正则表达式提取器和处理json-json path extractor）和jmeter操作数据库等等。

## Jmeter安装
官网：http://jmeter.apache.org/
下载：apache-jmeter-3.3.zip  （当前最新版本）
安装方法：解压缩即可
前提：JMeter是基于Java的桌面应用，需要安装JDK（1.6版本以上），并配置好JDK的环境变量JAVA_HOME
启动方式：在JMeter的bin目录下
    jmeter.bat （适用于Windows批处理文件）--双击即可启动JMeter
    jmeter.sh （适用于Linux的脚本文件）

## Jmeter接口测试

一般分五个步骤:

（1）添加线程组
![](/bimg/17.png)
（2）添加http请求 
![](/bimg/18.png)
（3）在http请求中写入接入url、路径、请求方式和参数 
	以百度的一个页面为例：https://p.baidu.com/daily/view?id=112389
	![](/bimg/19.png)
（4）添加查看结果树 
	![](/bimg/20.png)

（5）调用接口、查看返回值

接口请求后，可在“查看结果树”中查看接口返回状态和响应数据。
![](/bimg/21.png)
