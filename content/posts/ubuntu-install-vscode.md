---
title: "Ubuntu快速安装VSCode"
date: 2021-01-25T18:08:49+08:00
draft: false
categories: ["develop"]
lightgallery: false
tags: ["ubuntu", "install", "vscode"]
---
## 官网下载安装包安装

### 下载

[code.visualstudio.com](https://code.visualstudio.com/download)

ubuntu系统内下载缓慢时，可借用windows迅雷加速下载。

### 安装

```Shell
sudo  dpkg  -i code_1.52.1-1608136922_amd64.deb
```
## 使用umake安装

### 简单介绍

[Ubuntu Make](https://github.com/ubuntu/ubuntu-make) 原名 Ubuntu Developer Tools Center，是一款开源的命令行工具软件，用户可在主要 Linux 平台上轻易的进行安装，以开发 Android 应用。

随着不断发展，Ubuntu Make 现在已经包含很多的ide和软件开发工具。

### 安装umake命令

Ubuntu 用户安装命令：
```Shell
sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
sudo apt-get update
sudo apt-get install -y ubuntu-make
```
卸载 umake 命令：
```Shell
sudo apt-get remove ubuntu-make
```
使用说明：
```Shell
sudo umake --help
```

安装 GO 命令：
```Shell
sudo umake go go-lang
```
安装Arduino IDE 命令：
```Shell
sudo umake ide arduino
```
安装 Android Studio 命令：
```Shell
sudo umake android android-studio
```

### 安装VSCode

安装命令
```Shell
sudo umake ide visual-studio-code
```
提示输入a接受，安装完后，提示软件安装路径；

系统重启，软件市场出现VSCode图标。

## 结束语

> IDE开发工具选择VSCode，原因非常简单--跨平台，版本控制、编译测试、部署环境界面统一。