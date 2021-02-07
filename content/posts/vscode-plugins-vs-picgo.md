---
title: "VSCode的PicGo插件配置"
date: 2021-01-19T18:18:28+08:00
draft: false
categories: ["software"]
lightgallery: true
tags: ["应用", "vc-picgo", "VSCode", "Github"]
---
## 官方内容
### 概述
[vs-picgo](https://github.com/PicGo/vs-picgo) VSCode的PicGo插件。
### 插件安装
VSCode扩展中查找picgo，点击安装即可。

![vc-picgo插件安装](https://cdn.jsdelivr.net/gh/qimage/211@main/vscode-plugins-vs-picgo-01.jpg)

### Github设置
#### 设备仓库名

<用户名>/<仓库名>

#### 设定分支名

github默认为main

#### 获取Github token

Github / Settings / Developer settings / Personal access tokens

![获取token](https://cdn.jsdelivr.net/gh/qimage/211@main/how-to-upload-images-by-picgo-02.png)

点击Generate new token，填写Note，把repo的勾打上。

翻到页面底部，点击Generate token的绿色按钮生成token。

#### 设定自定义域名

https://cdn.jsdelivr.net/gh/<用户名>/<仓库名>@<分支名>

> https://cdn.jsdelivr.net/gh/ 可替换其他CDN域名前缀

![Github设置](https://cdn.jsdelivr.net/gh/qimage/211@main/vscode-plugins-vs-picgo-02.jpg)

### 插件使用
#### 从剪贴板上传图片到图床
Windows/Unix: Ctrl + Alt + u

OsX: Cmd + Opt + u
#### 从资源管理器上传图片到图床
Windows/Unix: Ctrl + Alt + e

OsX: Cmd + Opt + e
#### 从输入框中输入图片名称上传
Windows/Unix: Ctrl + Alt + o

OsX: Cmd + Opt + 0

这个快捷键可能与其他软件快捷键冲突。
## 结束语
> VSCode PicGo插件更新很快，使用非常简便；但上传错误需要修改删除时，需要使用[PicGo软件](/how-to-upload-images-by-picgo/)对图床照片进行管理操作。