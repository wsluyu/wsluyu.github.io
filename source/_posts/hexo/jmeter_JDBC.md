---
title: Jmeter连接数据库
categories: Jmeter
tags: Jmeter MySQL
date: 2018-04-16
---
Jmeter连接数据库

<!-- more -->

## 下载JDBC驱动
  在使用jmeter做性能或自动化测试的时候，往往需要直接对数据库施加压力，或者某些参数只能从数据库获取，这时候就必须使用jmeter连接数据库。

### 下载对应的驱动包

mysql驱动：
下载链接：https://dev.mysql.com/downloads/connector/j/
（mysql-connector-java-5.1.13-bin.jar 可能现在有跟新的版本了），并放到Jmeter目录中的lib文件下，复制之后，重启jmeter。

sqlServer驱动：
sqljdbc4.jar，一样都需要放到Jmeter目录中的lib文件下，复制之后，重启jmeter。

## 连接MySQL设置
### 1、配置驱动程序，测试计划右下角，点击浏览，选择jdbc驱动，如下图所示：
![](/bimg/25.png)

### 2、添加线程组
打开JMeter,创建线程组。鼠标右键点击测试计划--->添加--->Threads--->线程组。

### 3、配置JDBC

在线程组中，右键添加-->配置元件--->“JDBC Connection Configuration”，如下图所示：
![](/bimg/26.png)

### 4、配置JDBC Connection Configuration，如下图所示：

1)Varible Name: 这个是变量的名字，也就是说不能重复，

2) JDBC URL: jdbc:mysql://1920168.0.1:3306/idmdb ，其中 1920168.0.1:3306：这个数据库的地址和端口号； idmdb，这个是测试的数据库名。

3) Driver Class ：org.gjt.mm.mysql.Driver  或者 com.mysql.jdbc.Driver   这是固定值

4) Username：这个数据库的登录名

5) password： 这个是数据库的登录密码
![](/bimg/27.png)

### 5、添加JDBC request

右键点击“线程组”，在下面添加一个“JDBC request”，其中variable name名称必须与jdbc配置相同，如下图所示：

![](/bimg/28.png)

### 6、执行结果，如下图所示：

![](/bimg/29.jpg)