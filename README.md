在 macOS 上用 Hexo 搭建个人静态博客，采用 Hexo + GitHub Pages 的搭配，并使用七牛云作为图片存储工具，博客搭建过程大致是这样的：本地开发环境配置，编写代码并测试，使用 git 提交到 GitHub，绑定域名即可访问

参考：

- [Hexo 官方文档](https://hexo.io/zh-cn/docs/)

- [GitHub Pages 帮助文档](https://help.github.com/categories/github-pages-basics/)


## 环境准备

根据 Hexo 官方文档的描述，在使用 Hexo 之前需要现在系统中安装 Git 和 Node.js ，在 macOS 和 Linux 系统中自带有 Git，因此不需要进行额外的安装配置，而 Node.js 就需要下载安装，如果之前没有使用过 Node.js，有两个工具可能比较陌生：nvm 和 npm

 - **nvm** (Node Version Manager): Node 的版本管理工具，可以用 nvm 来下载任何版本的 Node.js 并切换 Node.js 的使用版本。nvm 不支持 Windows 系统，支持 macOS 和类 Linux 系统。要安装 nvm 的系统必须有 C++ 编译器。


- **npm** (Node Package Manager): 是一个下载和管理 Node.js 依赖包的工具，开发过程中如果需要其他的依赖包可以用 npm 来下载


### 安装 Node

如果不需要多个 Node 版本之间切换，可以不用安装 nvm，直接在 [Node 官网](https://nodejs.org/en/)下载并安装 Node 即可,通常安装 Node.js 的同时会自动安装 npm，安装完成后，在命令行中检查是否已安装

```
node --version

npm --version

```



### 安装 Hexo

系统中已经有 Git 和 Node 之后，就可以开始安装 Hexo 了：

```
npm install -g hexo-cli

```

## 搭建博客

环境准备完成后，就可以开始在本地搭建博客了，首先确定目录，例如我准备将 `~/Dev/Web/Hexo/` 作为本地博客的目录，先定位到目录：

```
cd ~/Dev/Web

```

然后执行：

```
hexo init Hexo

```


等待安装完成，会发现 `Hexo` 目录下新增了许多文件，这些都是 `Hexo` 自动生成的，接下来再执行：

```
npm install

```

然后博客就基本搭建完成了，通过 hexo 命令就能管理本地博客，例如启动本地服务器：

```
# 生成静态文件

hexo g

# 启动本地服务器

hexo s

```

在浏览器中访问 `http://localhost:4000` 就能看到 Hexo 生成的博客网站

## 配置

现在，已经可以在本地访问博客了，接下来要进行一些配置，然后提交到 GitHub 上，这样，通过访问 `http://classTC.github.io` 这样的 URL 时就能访问到博客。通过 GitHub Pages 中的帮助文档可以知道，必须创建一个以自己用户名命名，并以`.github.io` 为后缀的项目，例如上面的 `classTC.github.io` 这样的项目。

GitHub 上创建好项目后，在本地 `Hexo` 目录下的 `_config.yml` (这是项目跟目录下的配置文件，用户配置整个博客的，在每一个单独的 Theme 中还有一个 `_config.yml`，那是配置主题的) 的最下面添加如下内容：
```
deploy:
  type: git
  repository: git@github.com:classTC/classTC.github.io.git
  branch: master
```
然后，需要安装 git 插件：

```
npm install hexo-deployer-git --save
```

按照上面的操作完成后，执行：
```
hexo d
```
就能将本地文件提交到 GitHub 仓库中，并通过 `http://classTC.github.io` 这个 URL 访问博客

`_config.yml` 配置文件中还有许多对博客的配置，包括 URL，目录等各项配置

原文链接：https://github.com/classTC/classTC.github.io
