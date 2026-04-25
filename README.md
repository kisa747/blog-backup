# 说明文档

[![Pages](https://github.com/kisa747/blog-backup/actions/workflows/pages.yml/badge.svg)](https://github.com/kisa747/blog-backup/actions/workflows/pages.yml)

> 旧博客存档

## 部署

安装全局依赖

```sh
# 安装最新的 nodejs 长期支持版本
scoop install nodejs-lts
# 更换淘宝源
npm config set registry https://registry.npmmirror.com
# 全局安装Hexo，为了能够使用hexo命令。
npm install hexo-cli -g
```

克隆项目，安装项目依赖

```sh
# 克隆项目
git clone git@github.com:kisa747/blog-backup.git
cd blog-backup

# npm 安装需要的组件
npm install
```

然后就可以正常预览博客，或是生成静态文件

````sh
# 本地预览
start http://localhost:4000
hexo clean && hexo server

# 生成静态网站文件。生成至 public 文件夹下
hexo clean && hexo generate
````

## 发布

### 方法一、使用 Github Actions 发布

🚀 推荐使用此方法，简单方便。

* 在项目仓库目录下创建 `.github/workflows/pages.yml`，内容参考本仓库该 [文件](https://github.com/kisa747/blog-backup/actions/workflows/pages.yml)

* 然后配置 Github Actions：Github - Pages - Build and deployment - Source 设置为 `Github Actions`

### 方法二、一键部署

Github - Pages - Build and deployment - Source 设置为 `Deploy from a branch`

本地生成静态网址文件，然后推送至指定仓库。

首先配置仓库信息，编辑 `_config.yml` 

```yaml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
# username换成自己的用户名和仓库名,去掉括号
deploy:
    type: git
    repo: git@github.com:*/blog-backup.git
    branch: gh-pages
```

然后一键发布

```sh
# 生成静态网站文件并发布至指定仓库
hexo clean && hexo deploy --generate
```

### 方法三、手动发布

手动将 `public` 目录下文件推送至仓库，或是拷贝至服务器。
