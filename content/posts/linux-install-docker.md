---
title: "Ubuntu安装docker的方法"
date: 2020-01-14T11:04:49+08:00
draft: false
categories: ["develop"]
lightgallery: false
tags: ["安装", "ubuntu", "docker"]
---
## 检查内核docker支持
```SHELL
curl -L https://raw.githubusercontent.com/docker/docker/master/contrib/check-config.sh | /bin/bash /dev/stdin
```
## 安装docker
### 官方安装
参照<https://docs.docker.com/engine/install>
### 1: 安装工具
```Shell
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```
> H6加载aufs
```Shell
sudo apt-get -y install aufs-tools
```
### 2: 安装GPG证书
```Shell
curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
```
### 3: 写入软件源信息
#### amd64
```Shell
sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
```
#### arm64
```Shell
sudo add-apt-repository "deb [arch=arm64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
```
### 4 安装软件
```Shell
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
### 5: 查找特定版本
```Shell
sudo apt-get update
sudo apt-cache madison docker-ce
```
### 阿里云镜像安装
#### 版本选择
> H6核心版内核可使用最高版本
```Shell
export VERSION="5:19.03.5" 
```
#### 安装
```SHELL
curl -fsSL https://get.docker.com | bash -s docker –mirror Aliyun
```
## 版本验证
```SHELL
docker info
```
## 镜像加速设置
您可以通过修改daemon配置文件/etc/docker/daemon.json来使用加速器
```Shell
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://registry.docker-cn.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```
官方国内镜像  <https://registry.docker-cn.com>

网易         <http://hub-mirror.c.163.com>

中国科技大学  <https://docker.mirrors.ustc.edu.cn>
## 查看docker运行状态
```Shell
sudo docker info
sudo systemctl status docker 
```
## 常用命令
例子：在后台运行nginx，并将容器的80端口映射为宿主机的91端口。
```SHELL
docker run -d -p 91:80 nginx
```
> -d：后台运行 -P：随机端口映射 -p：指定端口映射 -net：网络模式

·  docker ps：列出运行中的容器

·  docker ps -a ：列出所有的容器

·  docker stop 容器id：停止容器

·  docker kill 容器id：强制停止容器

·  docker start 容器id：启动已停止的容器

·  docker inspect 容器id：查看容器的所有信息

·  docker container logs 容器id：查看容器日志

·  docker top 容器id：查看容器里的进程

·  docker exec -it 容器id /bin/bash：进入容器

·  exit：退出容器

·  docker rm 容器id：删除已停止的容器

·  docker rm -f 容器id：删除正在运行的容器
