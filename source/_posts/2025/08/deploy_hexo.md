---
layout: post
title:  Hexo 部署指南
date: 2025-08-06 22:09
categories: 技巧分享
tags: [hexo]
---

## 本地部署

```sh
# 安装最新的 nodejs 长期支持版本
scoop install nodejs-lts
# 持久使用淘宝源
npm config set registry https://registry.npmmirror.com
# 全局安装 Hexo，为了能够使用 hexo 命令。
npm install hexo-cli -g
# 初始化 Hexo（在 blog 空目录下执行，作为仓库根目录）
cd blog
hexo init
# 创建网站，npm 将会自动安装你需要的组件，只需要等待 npm 操作即可。
npm install
# 局部安装 Git 部署工具
npm install hexo-deployer-git
# 局部安装服务器模块
npm install hexo-server
# 安装主题
npm install hexo-theme-fluid

# 本地预览
start http://localhost:4000
hexo clean && hexo server

# 生成静态网站文件。生成至 public 文件夹下
hexo clean && hexo generate
```

## 发布至网络

### 方法一、使用 Github Actions 发布

参考：<https://hexo.io/zh-cn/docs/github-pages>

Github - Pages - Build and deployment - Source 设置为 `Github Actions`

🚀 推荐使用此方法，在项目仓库目录下创建 `.github/workflows/pages.yml`，内容参考本仓库该文件

### 方法二、一键部署

Github - Pages - Build and deployment - Source 设置为 `Deploy from a branch`

本地生成静态网址文件，然后推送至指定仓库。`_config.yml` 配置文件中配置好仓库信息：

```yaml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
# username 换成自己的用户名和仓库名，去掉括号
deploy:
    type: git
    repo: git@github.com:**/**.git
    branch: gh-pages
```

然后一键发布

```sh
# 生成静态网站文件并发布至指定仓库
hexo clean && hexo deploy --generate
```

### 方法三、手动发布

手动将 `public` 目录下文件推送至仓库，或是拷贝至服务器。
