---
title: "PicGo图床软件的配置与使用"
date: 2021-01-18T18:18:28+08:00
draft: false
categories: ["software"]
lightgallery: true
tags: ["应用", "PicGo", "Github"]
---
## 官方内容
### 概述
[PicGo](https://github.com/Molunerfinn/PicGo) 一个用于快速上传图片并获取图片 URL 链接的工具。
PicGo 支持如下图床：
* [七牛图床](https://www.qiniu.com/products/kodo)
* [腾讯云 COS](https://cloud.tencent.com/product/cos)
* [又拍云](https://www.upyun.com/products/file-storage)
* [GitHub](https://github.com/)
* [SM.MS](https://sm.ms/)
* [阿里云 OSS](https://www.aliyun.com/product/oss)
* Imgur
### 下载安装
点击此处下载 [应用](https://github.com/Molunerfinn/PicGo/releases)
### 应用截图
![PicGo 截图](https://raw.staticdn.net/Molunerfinn/test/master/picgo/picgo-2.0.gif)

[更多内容](https://picgo.github.io/PicGo-Doc)
## 应用设置
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

![Github设置](https://cdn.jsdelivr.net/gh/qimage/211@main/how-to-upload-images-by-picgo-01.png)

### 腾讯云COS设置
#### 新建用户
右上角帐户 / 访问管理 / 用户 / 用户列表 / 新建用户

![新建用户](https://cdn.jsdelivr.net/gh/qimage/211@main/how-to-upload-images-by-picgo-03.png)

访问控制选择编程方式，

用户权限选择QcloudCOSFullAccess，

其他均不勾选，点击创建用户。

#### 用户访问信息

查看用户，获取用户信息。

![用户相关信息](https://cdn.jsdelivr.net/gh/qimage/211@main/how-to-upload-images-by-picgo-06.png)

获取SecretId、SecretKey、APPID

#### 创建存储桶
控制台 / 对象存储 / 存储桶列表 / 创建存储桶

![创建存储桶](https://cdn.jsdelivr.net/gh/qimage/211@main/how-to-upload-images-by-picgo-08.jpg)

获取存储空间名与存储区域

![查看信息](https://cdn.jsdelivr.net/gh/qimage/211@main/how-to-upload-images-by-picgo-07.jpg)

#### 填写相关设置
填写腾讯云COS设置

![腾讯云COS设置](https://cdn.jsdelivr.net/gh/qimage/211@main/how-to-upload-images-by-picgo-05.png)

如果使用CDN，可以设定自定义域名
## 使用
PicGo上传图片得到图床图片网络链接，有5种链接格式，可配合各种md编辑器使用。
## 结束语
> 如果是国外静态网站，图床推荐使用Github；如果是国内备案网站，可以使用腾讯COS+CDN，流量花费也不是很高。