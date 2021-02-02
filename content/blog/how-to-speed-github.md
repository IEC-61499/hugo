---
title: "国内加速Github的几种方案"
date: 2021-01-01T11:08:49+08:00
draft: false
categories: ["network"]
tags: ["加速", "github", "cdn"]
---
## GitHub 镜像访问

国内最常用的镜像地址：

### 1. [github.com.cnpmjs.org](https://github.com.cnpmjs.org)

### 2. [hub.fastgit.org](https://hub.fastgit.org) (推荐)

### 3. [gitclone.com](https://gitclone.com)

网站的内容与GitHub完整同步，可进行下载克隆等操作。

#### 仓库克隆下载

原地址

```Shell

git clone https://github.com/docker/compose.git

```

改为

```Shell

git clone https://github.com.cnpmjs.org/docker/compose.git

```

或者

```Shell

git clone https://hub.fastgit.org/docker/compose.git

```

或者

```Shell

git clone https://gitclone.com/github.com/docker/compose.git

```

#### Release下载加速

原地址

```Shell

wget https://github.com/golang/go/archive/go1.15.7.tar.gz

```

改为

```Shell

wget https://hub.fastgit.org/golang/go/archive/go1.15.7.tar.gz

```

#### 免替换法

```Shell

git config --global url."https://hub.fastgit.org".insteadOf https://github.com

```

#### 查看git配置信息

```Shell

git config --global --list

```

#### 取消设置

```Shell

git config --global --unset url.https://github.com/.insteadof

```

## raw文件下载加速

将 raw.githubusercontent.com 替换为 raw.staticdn.net 即可加速。

原地址：

```Shell

wget https://raw.githubusercontent.com/kubernetes/kubernetes/master/README.md

```

替换为

```Shell

wget https://raw.staticdn.net/kubernetes/kubernetes/master/README.md

```

## GitHub + Jsdelivr CDN加速

[jsDelivr](https://www.jsdelivr.com/) 是一个免费开源的CDN 解决方案；

包含 JavaScript 库、jQuery 插件、CSS 框架、字体等常用的静态资源；

jsdelivr 不能获取 exe 文件以及 Release 处附加的 exe 和 dmg 文件。

### 1. 直接引用(临时)

格式为：

https://cdn.jsdelivr.net/gh/<用户名>/<仓库名>/<文件及路径>

例如：GitHub

<https://github.com/qimage/pub/blob/main/avatar.webp>

转成 jsdelivr

<https://cdn.jsdelivr.net/gh/qimage/pub/avatar.webp>

github.com 替换成 cdn.jsdelivr.net/gh

/blob/main 删除

### 2. 引入版本号(推荐)

版本号用@符链接，格式为：

https://cdn.jsdelivr.net/gh/<用户名>/<仓库名>@版本号/<文件及路径>

例如：GitHub

<https://github.com/qimage/pub/blob/main/avatar.webp>

转成 jsdelivr

<https://cdn.jsdelivr.net/gh/qimage/pub@main/avatar.webp>

github.com 替换成 cdn.jsdelivr.net/gh

/blob/ 替换成 @ 

注：main为创建的版本号

建议使用发布版本号方案，只要单次版本号下的内容大小不超过50M即可，超过50M时使用多版本号。

{{< admonition tip >}}

需要jsDelivr缓存实时刷新，只需将想刷新的链接的开头的

```

https://cdn.jsdelivr.net/

```

替换成

```

https://purge.jsdelivr.net/

```

即可实时刷新，刷新成功后，浏览器会返回缓存刷新成功的信息。

{{< /admonition >}}

## 修改HOSTS文件进行加速

### 1. 查询相关域名IP地址

通过 [ipaddress.com](https://www.ipaddress.com/) 查询

[github.global.ssl.fastly.net](https://fastly.net.ipaddress.com/github.global.ssl.fastly.net)

[github.com](https://github.com.ipaddress.com/)

### 2. 修改host文件映射查找到的IP地址

windows系统中修改C:\Windows\System32\drivers\etc\hosts文件的权限，指定可写入；

ubuntu系统中修改/etc/hosts文件；

用编辑器打开hosts文件，在末尾处添加以下内容：

```

199.232.69.194 github.global.ssl.fastly.net
140.82.112.4 github.com

```

同时也可以查询其他域名地址，解决DNS污染问题。

可以直接选中以下内容复制粘贴，20210126更新

```

# GitHub Start 
140.82.113.3       github.com
140.82.114.20      gist.github.com
151.101.184.133    assets-cdn.github.com
151.101.184.133    raw.githubusercontent.com
199.232.28.133     raw.githubusercontent.com 
151.101.184.133    gist.githubusercontent.com
151.101.184.133    cloud.githubusercontent.com
151.101.184.133    camo.githubusercontent.com
199.232.96.133     avatars.githubusercontent.com
151.101.184.133    avatars0.githubusercontent.com
199.232.68.133     avatars0.githubusercontent.com
199.232.28.133     avatars0.githubusercontent.com 
199.232.28.133     avatars1.githubusercontent.com
151.101.184.133    avatars1.githubusercontent.com
151.101.108.133    avatars1.githubusercontent.com
151.101.184.133    avatars2.githubusercontent.com
199.232.28.133     avatars2.githubusercontent.com
151.101.184.133    avatars3.githubusercontent.com
199.232.68.133     avatars3.githubusercontent.com
151.101.184.133    avatars4.githubusercontent.com
199.232.68.133     avatars4.githubusercontent.com
151.101.184.133    avatars5.githubusercontent.com
199.232.68.133     avatars5.githubusercontent.com
151.101.184.133    avatars6.githubusercontent.com
199.232.68.133     avatars6.githubusercontent.com
151.101.184.133    avatars7.githubusercontent.com
199.232.68.133     avatars7.githubusercontent.com
151.101.184.133    avatars8.githubusercontent.com
199.232.68.133     avatars8.githubusercontent.com
199.232.96.133     avatars9.githubusercontent.com
# GitHub End

```

### 3. 本地DNS刷新

windows中若遇到网络异常，可能是DNS缓存的问题，可以命令刷新。

```Shell

ipconfig /displaydns # 显示dns缓存 
ipconfig /flushdns   # 刷新DNS记录
ipconfig /renew      # 重请从DHCP服务器获得IP

```

ubuntu中重启网络

```Shell

sudo /etc/init.d/networking restart

```

## 通过 Gitee 导入Github仓库进行中转下载

访问 [gitee](https://gitee.com/) 并登录，在顶部选择“从 GitHub/GitLab 导入仓库”。

导入后，若源站更新，Gitee导入仓库需要强制更新同步。

[Gitee 极速下载](https://gitee.com/mirrors)，热门仓库每日同步一次。

## GitHub 文件加速

利用 Cloudflare Workers提供GitHub 文件 , Releases , archive 以及 raw.githubusercontent.com 文件加速下载服务。

开源项目地址: <https://github.com/hunshcn/gh-proxy>

部署独立地址: <https://ghproxy.com/>

## 结束语

> 以上方案为均来自网络，结合操作实验整理而成。
