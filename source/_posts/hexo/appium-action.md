---
title: Appium使用教程基于Python
categories: appium
tags: appium
date: 2022-01-01
---

![](/bimg/53.png)

## 一、Appium简介

### 1. Appium简介

Appium是一个开源测试自动化框架，可用于原生，混合和移动Web应用程序测试。 它使用WebDriver协议驱动iOS，Android和Windows应用程序。

Appium的优势：
- 可以跨平台同时支持Android、iOS 
- 支持多种语言，java、python、php、Ruby等

### 2. Appium的架构

1. Appium有客户端和服务器两部分组成
2. Appium是在手机操作系统自带的测试框架基础上实现的
3. Android：UIAutomator
4. iOS:UIAutomation

**Appium运行原理**

![](/bimg/41.png)

1. 我们的电脑上运行自动化测试脚本（client），调用的是 webdriver 的接口，appium server接收到我们 client 上发送过来的命令后他会将这些命令转换为 UIIautomator 认识的命令，然后由 UIautomator 来上设备上执行自动化。
2. Appium 的架构原理如上图所示，由客户端（Appium Client）和服务器（Appium Server）两部门组成，客户端与服务器通过 JSON Wire Protocol 进行通信。

## 二、Appium环境搭建

按下面安装环境为例：
- 操作系统：Mac
- 被测平台：Android模拟器或Android真机
- appium服务端：appium Desktop
- appium客户端：python-client

### 1.使用Android Studio创建Andorid模拟器
#### (1)Andriod studio下载
https://developer.android.google.cn/studio
据自己的操作系统下载对应版本，我用的是mac

#### (2)创建Andorid模拟器
1. 首先，启动Android Studio ，创建一个项目，然后点击下面按钮，进入创建模拟器管理页面

![](/bimg/49.png)

2. 点击Create Virtual Device创建模拟器
category选择phone，然后选择一款手机型号

![](/bimg/50.png)

AVD Name:为模拟器起一个名字
Pixel 2 XL: 选择手机型号，屏幕尺寸为5.99英寸，分辨率为1440*2880（单位：像素），560dpi
Q:对应的Android版本10.0  x86
Startup orientation:选择模拟器横屏或者竖屏显示
Graphics:选择模拟器中的渲染图形
Device Frame:是否显示手机外形，可以不勾选。
单击Finish按钮，完成Android模拟器的创建。

![](/bimg/51.png)

在Android模拟器管理列表中，选择创建的Android模拟器，在Actionsy一列中单机三角形启动按钮，启动模拟器

<img src="/bimg/52.png" width="500">

### 2.Appium Desktop
appium下载地址：https://github.com/appium/appium-desktop

可以根据自己的平台下载相应的版本。下面以Mac版本为例，下载并安装完成后，appium启动界面如下：

<img src="/bimg/42.png" width="400">

默认显示监控的Host和Port，点击start server按钮，启动server，监听本机的4732端口。

<img src="/bimg/43.png" width="500">

启动观察器

### 3.Python Client

前提：系统已经安装并配置好python环境

方法1：直接用pip命令安装

```bash
$ pip install Appium-Python-Client 
```

方法2： 官方下载 Appium-Python-Client包，命令行进入解压目录，运行

```bash
$ python setup.py install 
```

### 4.连接Android真机
使用数据线把手机连接到开启appium的电脑，开启usb调试功能。可使用adb命令列出设备确保连接成功

```bash
$ adb devices -l
```

举例如下：

![](/bimg/44.png)

设备名 device:star2qlteue 

## 三、Appium基础

### 1.Desired Capabilities
appium在启动session时，需要提供Desired Capabilities。Desired Capabilities本质上是字典对象，由客户端生成并发送给服务器（appium desktop）,告诉服务器APP运行的环境。

Desired Capabilities基本配置：

```python
desired_caps = { 
    'automationName': 'appium', 
    'platformName': 'Android', 
    'deviceName': 'star2qlteue', 
    'appPackage': 'com.包名x.包名y', 
    'appActivity': 'com.包名x.包名y.view.base.首页Activity', 
    'noReset': False  # 启动APP是不是需要清除原有数据 
}
```

如何获取'appPackage'和'appActivity'

1. 打开APP。
2. 执行> adb logcat>./log.txt
3. 在APP上做一些操作
4. Ctrl+c 结束adb命令
5. open log.text 打开文件，搜索：Displayed 

### 2.元素定位

UI自动化测试关键就是定位元素，想要对元素进行点击或输入操作，都要定位元素。
常用的定位方法：

- id定位

```py
driver.find_element(
    AppiumBy.ID,
    "com.sixdays.包名x.包名y:id/iv_close"
)
```

- Class name定位

```py
driver.find_element(AppiumBy.CLASS_NAME, "android.widget.Button")
```

- Accessibility id定位

```py
driver.find_element(AppiumBy.ACCESSIBILITY_ID, "ACCESSIBILITY_ID")
```

- Android uiautomtor定位

```py
driver.find_element_by_android_uiautomator(
    'new UiSelector().text("Suggest an Edit")'
)
```

- Xpath定位

```py
driver.find_element(
    AppiumBy.XPATH,
    "//android.view.ViewGroup/android.widget.Button"
)
```

### 3.appium常用API
appium官方文档：http://appium.io/docs/en/about-appium/intro/

应用操作：
1. 安装应用：install_app()
2. 卸载应用：remove_app()
3. 关闭应用：close_app()
4. 启动应用：lanch_app()
5. 将应用置于后台：background_app()

键盘操作：
1. 输入字符串：send_keys()
2. 模拟键盘：keyevent()

触摸操作：
1. 点击操作：click()
2. 长按控件：long_press()
3. 移动：move_to()

## 四、unittest单元测试框架

### 1. unittest是什么
unittest是python内置的单元测试框架，具备编写用例、组织用例、执行用例、输出报告等自动化框架的条件。

### 2. 单元测试框架提供的功能

1. 提供用例组织与执行

    当测试用例达到成百上千条时，就产生了扩展性与维护性等问题，此时就需要考虑用例的规范与组织问题了。单元测试框架便能很好的解决这个问题

2. 提供丰富的断言方法

    不论是功能测试还是单元测试，在用例完成之后都需要将实际结果与预期结果进行比较(断言)，从而断定用例是否执行通过。单元测试框架一般会提供丰富的断言方法。例如：相等\不相等，包含\不包含，True\False的断言方法等

3. 提供丰富的日志

    当测试用例执行失败时能抛出清晰的失败原因，当所有用例执行完成之后能提供丰富的执行结果。例如，总执行时间、失败用例数、成功用例数等

### 3. 重要的概念

1. Test case

    一个TestCase的实例就是一个测试用例。什么是测试用例呢？就是一个完整的测试流程。包括测试前准备环境的搭建(SetUP)、实现测试过程的代码(run)，以及测试后环境的还原(tearDown)。单元测试(Unittest)的本质也就在这里，一个测试用例就是一个完整的测试单元，通过运行这个测试单元，可以对某一个功能进行验证
    
2. Test Suite

    一个功能的验证往往需要多个测试用例，可以把多个测试用例集合在一起执行，这就产生了测试套件TestSuite的概念。TestSuite用来组装单个测试用例。可以通过addTest加载TestCase到TestSuite中，从而返回一个TestSuite实例。而且TestSuite也可以嵌套TestSuite

3. Test Runner

    测试的执行也是单元测试中非常重要的一个概念，一般单元测试框架中都会提供丰富的执行策略和执行结果。在Unittest单元测试框架中，通过TextTestRunner类提供的run()方法来执行test suite/test case。test runner可以使用图形界面、文本界面，或返回一个特殊的值等方式来表示测试执行的结果

4. Test Fixture

    对一个测试用例环境的搭建和销毁，就是一个Fixture，通过覆盖TestCase的setUP()和tearDown()方法来实现。这有什么用呢？比如说在这个测试用例中需要访问数据库，那么可以在setUP()中建立数据库连接来进行初始化，在tearDown()中清除数据库产生的数据，然后关闭连接

    注：tearDown()方法的过程很重要，要为下一个TestCase留下一个干净的环境

![](/bimg/45.png)

### 4. 断言方法

在执行测试用例的过程中，最终的测试用例执行成功与否，是通过测试得到的实际结果与预期结果进行比较得到的。unittest框架的Testcase类提供的用于测试结果的常用断言方法如下：

| assertEqual(a,b)    | a == b        |
| ------------------- | ------------- |
| assertNotEqual(a,b) | a != b        |
| assertTrue(x)       | x is true     |
| assertFalse(x)      | x is false    |
| assertIsNone(x)     | x is none     |
| assertIsNotNone(x)  | x is not none |

## 五、HTML测试报告

HTMLTestRunner是unittest的一个扩展，它可以生成易于使用的HTML测试报告。
下载地址：http://tungwaiyip.info/software/HTMLTestRunner.html

生成HTML测试报告：

```py
with(open('./test.html', 'wb')) as fp:
    runner = HTMLTestRunner(
        stream=fpz,
        title='<project name>test report',
        description='describe: TP test '
    )
    runner.run(suite)
```

测试报告展示：

![](/bimg/46.png)

![](/bimg/47.png)
