---
title: Python小程序
categories: Python
tags: Python
date: 2018-04-10
---
Python小程序

<!-- more -->
## 冒泡排序
下面是实现代码：

```python
list = [5,1,8,0]
for i in range(1,len(list)):  
    for j in range(0,len(list)-i):
        if list[j]>list[j+1]:
            temp = list[j]
            list[j] = list[j+1]
            list[j+1] = temp
print list
```

## 列表去重
下面是实现代码：

```python
list = [1, 1, 1, 2, 3, 2, 4, 5, 5]
res = []
for i in range(0,len(list)-1):
    if list[i] not in res:
        res.append(list[i])
print res
```
