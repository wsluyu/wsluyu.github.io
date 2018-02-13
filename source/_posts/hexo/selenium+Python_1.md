---
title: 编写一个自动化脚本
categories: 测试
tags: selenium,python
date: 2018-2-13
---
selenium+Python自动化测试

<!-- more -->

## ——第一个自动化脚本

推荐使用编程工具PyCharm

```python
#coding=utf-8  //把编码统一成utf-8格式。等号两边不要留空格，否则不起作用
from selenium import webdriver //导入selenium的WebDriver包

driver = webdriver.Chrome() //把WebDriver的Chrome对象赋值给变量driver
driver.get("https://www.baidu.com/") //获得浏览器对象后通过get()方法，向浏览器发送网址

driver.find_element_by_id("kw").send_key("selenium2") //定位元素，并向输入框输入selenium2
driver.find_element_by_id("su").click() //定位按钮，发送单击事件
driver.quit() //退出并关闭浏览器
```

## ——安装浏览器驱动

WebDriver支持 Firefox、IE、Opera和chrome等浏览器。它还支持Android和iPhone的移动应用测试。
各个浏览器驱动的下载地址：http://www.seleniumhq.org/download
安装chrome浏览器驱动，下载ChromeDriver_win32.zip(根据自己的系统下载)，解压得到chromedriver.exe文件，放到系统环境变量Path下面，之前已经将(C:\Python27)放到系统环境变量Path下面，所以将chromedriver.exe放到C:\Python27\ 目录下。
