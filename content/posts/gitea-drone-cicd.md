---
title: "基于Gitea与Drone的自动集成部署"
date: 2021-01-21T15:52:20+08:00
draft: false
tags: ["持续集成", "持续部署", "drone", "git"]
categories: ["develop"]
---
## 前言

### 1.Gitea介绍

Gitea可以像Github那样，管理公司的文档与代码类资产。

Gitea采用GO语言编写，是自助式、轻量级、遵循Git规范的代码托管工具。

Gitea官网：<https://gitea.io/zh-cn/>，Gitea官方文档：<https://docs.gitea.io/zh-cn/>

### 2.Drone介绍

Drone是基于Docker的CI/CD工具。Drone 所有编译、测试的流程都在容器中进行。

开发者只需在项目中包含 .drone.yml 文件，将代码推送到 git 仓库，Drone就能够自动化的进行编译、测试、发布。

官网：<https://drone.io/>，官方文档：<https://docs.drone.io/>

### 3.Drone优势

#### 流程定义简单

配置即为代码，用配置的方式简单明了定义流程，告别复杂的shell脚本。

#### 支持多硬件环境

Drone适合在各种平台运行，如Linux x64、ARM、ARM64、Windows x64。

#### 支持多种源代码管理系统

Drone支持各种多种主流的git源代码管理系统如 Github, Bitbucket, GitLab, GitTea。

#### 支持各种编程语言编程环境

Drone+docker基本可用于任何编程语言、任何数据，任何服务。

## 工作原理

1. git push提交代码（含有.drone.yml）到代码托管系统（GitHub、GitLab、Gitea等）

2. 代码托管系统通过 webhook 触发Drone的pipeline

3. 登录Drone平台执行pipeline，build构建项目

4. 构建Docker镜像（需要 Dockerfile 文件）

5. 自动将镜像发布至Docker仓库，或者部署工作（需要pipeline插件配置）

  ![Gitea+Drone平台网络架构](https://cdn.jsdelivr.net/gh/qimage/211@main/git_drone_architecture.jpg "Gitea+Drone平台网络架构")

## 结束语

> 专注代码，敏捷部署，配置即代码。

drone.yml + Dockerfile + docker-compse.yml三个文件自动完成代码编译测试、发布镜像、部署容器的整个开发流程。
