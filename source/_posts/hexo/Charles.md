---
title: Charles设置手机端代理
categories: 测试
tags: Charles
date: 2017-05-25
---
Charles设置手机端代理

<!-- more -->
目的：想在手机上访问代理地址
一、	在电脑上设置hosts代理地址如：52.9.163.97  luyu.chime.me
二、	打开Charles
三、	在 iPhone 的 “ 设置 “->” 无线局域网 “ 中，可以看到当前连接的 wifi 名，通过点击右边的详情键，可以看到当前连接上的 wifi 的详细信息，包括 IP 地址，子网掩码等信息。在其最底部有「HTTP 代理」一项，我们将其切换成手动，然后填上 Charles 运行所在的电脑的 IP，以及端口号 8888
![](/bimg/phone.png)
四、	手机保存设置后，Charles弹出授权弹窗，点击allow
![](/bimg/allow1.png)
五、	手机上访问网站，即可在Charles中看到请求
![](/bimg/allow2.png)