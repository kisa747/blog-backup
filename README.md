# 说明文档

[![Pages](https://github.com/kisa747/blog/actions/workflows/pages.yml/badge.svg)](https://github.com/kisa747/blog/actions/workflows/pages.yml)

> 旧博客存档，采用 Hexo 构建

## 部署

安装全局依赖

```sh
# 安装最新的 nodejs 长期支持版本
scoop install nodejs-lts
# 更换淘宝源
npm config set registry https://registry.npmmirror.com
# 全局安装 Hexo，为了能够使用 hexo 命令。
npm install hexo-cli -g
```

克隆项目，安装项目依赖

```sh
# 克隆项目
git clone <repo>
cd blog

# npm 安装需要的组件
npm install
```

然后就可以正常预览博客，或是生成静态文件

```sh
# 本地预览
start http://localhost:4000
hexo clean && hexo server

# 生成静态网站文件。生成至 public 文件夹下
hexo clean && hexo generate
```

更新依赖包

```sh
# 安装 ncu 命令
npm install -g npm-check-updates

# 检查工作区更新
ncu
# 更新 package.json
ncu -u
# 根据 package.json 更新依赖项
npm install
```

## 发布

### 方法一、使用 Github Actions 发布

🚀 推荐使用此方法，简单方便。

* 在项目仓库目录下创建 `.github/workflows/pages.yml`，内容参考本仓库该 [文件](https://github.com/kisa747/blog/actions/workflows/pages.yml)

* 然后配置 Github Actions：Github - Pages - Build and deployment - Source 设置为 `Github Actions`

### 方法二、手动发布

手动将 `public` 目录下文件推送至仓库，或是拷贝至服务器。
