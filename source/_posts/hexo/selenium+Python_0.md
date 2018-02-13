---
title: selenium+Python环境搭建
categories: 测试
tags: selenium,python
date: 2018-2-11
---
selenium+Python环境搭建

<!-- more -->

## ——安装Python

访问Python官方网站：https://www.python.org

找到下载页面，根据自己的平台选择相应的版本进行下载。Windows版本下载后会得到一个后缀名.msi的文件，双击安装。

安装过程与一般的Windows程序类似。安装完成后，会在开始菜单中看到安装好的Python目录。如图。
![](/bimg/22.png)

打开Python自带的IDLE，就可以编写Python程序了。Python Shell界面如图。
![](/bimg/23.png)

或者在Windows命令下输入“python”命令，也可以进入Python Shell模式。
![](/bimg/24.png)



## ——安装pip

pip是一个安装和管理Python包的工具，通过pip来安装Python包变的十分简单。
pip下载地址：https://pypi.python.org/pypi/pip
解压下载文件，通过Python命令执行setup.py进行安装。

在最新的Python安装包中已经集成了pip,可以在Python目录C:\Python27\Scripts下查看是否有pip.exe文件。

## ——安装selenium
cmd.exe:

	>pip install selenium==2.48.0 //指定版本号安装

	>pip uninstall selenium //卸载当前安装的包

