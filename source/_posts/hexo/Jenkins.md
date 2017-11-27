---
title: Jenkins环境搭建
categories: 测试
tags: Jenkins
date: 2017-11-27
---
Jenkins环境搭建

<!-- more -->

## 一、 java开发环境配置

### 1.安装jdk（java开发工具包）

双击jdk-7u13-windows-i586.exe，一路next。
安装路径不一定在默认路径，但要记住此安装路径

### 2.设置java环境变量

1)桌面[计算机]图标，右键选择属性->高级系统设置->环境变量
2) 选择系统变量->新建也可以新建成用户变量但是其他用户无法使用
变量名：JAVA_HOME
变量值：C:\Program Files (x86)\Java\jdk1.7.0_13这里是你上一步安装java的路径

![](/bimg/1.png)



3) 上步结束之后，选中环境变量中的“path”

![](/bimg/2.png)

选中之后编辑：![](/bimg/3.png)

“变量值”一栏的最后面添加如下的

;%Java_Home%\bin;%Java_Home%\jre\bin;

一个字不要差，注意前后都要有英文分号

4)上一步确定之后，再“新建”

![](/bimg/4.png)

变量名：CLASSPATH

变量值：.;%Java_Home%\bin;%Java_Home%\lib\dt.jar;%Java_Home%\lib\tools.jar

上面的变量值最好也是一个字符不变的贴上去，“变量值”最前面的 .; 不要漏掉

5)检查环境变量搭好了：调出“cmd”检查

输入java –version（提供给你们的版本应该是1.7.0.13）

![]()

 

输入java

![]()

输入javac

![]()

三张图都看到了，就说明java环境配置成功。

## 二、 tomcat安装与配置

1.解压apache-tomcat-7.0.68-windows-x64.zip

2. 配置环境变量：

变量名：CATALINA_HOME

变量值：刚刚安装的路径

3. bin 文件夹，找到里面的startup.bat，运行，最小化该窗口

4. 打开浏览器，输入http：//localhost:8080.如果出现下面的内容说明成功了

## 三、Jenkins安装

在最简单的情况下，Jenkins 只需要两个步骤：

1.下载一个WAR文件

2.运行 [**Java**](http://lib.csdn.net/base/17) -jar jenkins.war

 

还有一种安装方式就是将下载的war包文件部署到 servlet 容器tomcat/webapps目录下，在浏览器的URL地址栏中输入类似http://localhost:8080/jenkins/这样的地址即可。下图是安装成功后的界面