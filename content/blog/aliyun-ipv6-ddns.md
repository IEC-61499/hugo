---
title: "借用阿里云实现IPV6的动态域名解析"
date: 2020-01-13T11:04:49+08:00
draft: false
categories: ["network"]
tags: ["阿里云", "ipv6", "ddns"]
---
## 目标
由于电信运营商改造后IPV4变成内网固定IP，使得内网穿透变得更加麻烦。

虽然运营商提供的全网IPV6地址没有时间限制，但是断网后或者宽带重拔后IPV6依然会重新分配更新，所以还是需要使用IPV6动态域名解析。

## 原理
使用GO版本的客户端调用阿里云云解析API，实现IPV6的动态域名解析。

参照<https://github.com/honwen/aliyun-ddns-cli>实现。
## 阿里云设置
右上角用户 / 访问控制 / 人员管理 / 用户 / 创建用户

填写登录名称，显示名称，选择编程访问启用 AccessKey ID 和 AccessKey Secret；

记录AccessKey以便后面使用，设置用户权限为AliyunDNSFullAccess。

## 执行命令
环境变量：

AccessKeyID     阿里云访问ID

AccessKeySecret 阿里云访问密钥
```Shell
aliyun-ddns-cli --id ${AccessKeyID} --secret ${AccessKeySecret} --ipapi http://v6.ipv6-test.com/api/myip.php auto-update -6 --domain qu.js.cn -r 600
```
## 结束语
> 目前移动网络已支持IPV6，固定宽带需要路由器支持IPV6，80端口封禁，443端口有可能开启。