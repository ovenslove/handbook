React-native Android环境搭建.md
---

## 目录

- [基础安装](#基础安装)
  - [安装Homebrew](#安装homebrew)
  - [安装Node.js](#安装nodejs)
  - [安装watchman](#安装watchman)
  - [安装flow](#安装flow)
  - [安装react-native-cli](#安装react-native-cli)
- [iOS环境安装](#ios环境安装)
- [Android环境安装](#android环境安装)
  - [基础软件安装](#基础软件安装)
  - [环境变量配置](#环境变量配置)
  - [测试服务端](#测试服务端)
  - [启动步骤](#启动步骤)
- [参考资料](#参考资料)

## 基础安装

### 安装Homebrew

Homebrew是Mac OSX的包管理器，我们需要通过Homebrew安装开发React Native的相关软件包。
如果不知道怎样安装Homebrew可以点这里：[官网](http://brew.sh/index_zh-cn.html)。根据官网的介绍安装即可。

### 安装Node.js

```bash
$ brew install node
```

### 安装watchman

watchman是Facebook用于监视JavaScript文件改动的开源项目。

```bash
$ brew install watchman
```

### 安装flow

flow是Facebook开源的一个JavaScript静态类型检查器，用于发现JavaScript程序中的类型错误。

```bash
$ brew install flow
```

### 安装react-native-cli

react-native-cli是React Native的命令行工具，安装react-native-cli后我们就能够通过react-native相关命令管理ReactNative工程。

```bash
$ npm install -g react-native-cli
```

## iOS环境安装

相对于Android环境搭建，iOS简单太多了，太easy了！在基础环境安装成功之后，只需去[Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)下载Xcode，并安装Xcode即可，首次安装需要打开Xcode初始化。在初始化项目好之后，只需在项目根目录运行下面命令即可：

```bash
$ react-native run-ios`
```

## Android环境安装

在Android环境，比较难搞，按照步骤安装即可，不要放过任何步骤哦。

### 基础软件安装

1. 安装JDK [jdk-8u101-macosx-x64.dmg](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html)
  - 查看版本，命令行中运行`javac -version`
2. 安装Android Studio
  - 勾选`Performance`和`Android Virtual Device`
  - 安装相关`SDK Platforms `，记得勾选`Show Package Details`
  - 安装`SDK Tools` 必须是这个版本 `Android SDK Build-Tools 23.0.1`，记得勾选`Show Package Details`。
  - ANDROID_HOME环境变量设置。（见下面 环境变量配置）方法
3. 安装 [免费VirtualBox虚拟机](https://www.virtualbox.org/)
4. 安装模拟器[Genymotion](http://www.genymotion.net/)
  - 注册帐号
  - 下载Genymotion
  - 安装Genymotion

### 环境变量配置

你可以把`Android SDK`的`tools`和`platform-tools`目录添加到PATH变量中，以便在终端中运行一些Android工具，例如`android avd`或是`adb logcat`等。  

在`~/.bash_profile`中添加(如果你安装的 ZSH 则在 `~/.zshrc`中添加)：

```bash
PATH="~/Library/Android/sdk/tools:~/Library/Android/sdk/platform-tools:${PATH}"
export PATH
export ANDROID_HOME=~/Library/Android/sdk
```

改完需要运行`source ~/.bash_profile`
（注意：你的SDK的具体路径可能不同）

### 测试服务端

这时候可以用浏览器访问  
http://localhost:8081/index.android.bundle?platform=android  
如果可以访问表示服务器端已经可以了。

### 启动步骤

#### 启动 Genymotion 设置

在应用中登录，点击按钮`Add`下载模拟器设备，在`Setting`中设置`ADB`选择`User custom Android SDK tools.`填写地址，一般在目录`/Users/用户名/Library/Android/sdk`中，点击按钮`Start`启动模拟器

![](img/Genymotion01.jpg)
![](img/Genymotion02.jpg)
![](img/Genymotion03.jpg)

#### 运行命令启动项目

进入项目的根目录，也就是有`package.json`文件的目录，运行`react-native run-android`启动项目，如下动图：

![](img/React-native-run.gif)

### 报错

在Android环境下运行，会报下面错误，原因是没有连接手机会报如下错，**开发阶段可忽视**

```bash
error: no devices/emulators found
Could not run adb reverse: Command failed: ~/Library/Android/sdk/platform-tools/adb reverse tcp:8081 tcp:8081
```

## 参考资料

- [官方搭建开发环境](https://facebook.github.io/react-native/docs/getting-started.html#content)
- [reactnative.cn搭建开发环境](http://reactnative.cn/docs/0.35/getting-started.html)
- [极客学院搭建开发环境](http://wiki.jikexueyuan.com/project/react-native/DevelopmentSetupAndroid.html)
