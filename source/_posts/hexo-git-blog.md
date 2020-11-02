---
title: hexo+git blog
date: 2020-11-03 01:42:30
tags:
---

## 环境搭建

### 1、node.js

NodeJS官网下载对应系统的安装包安装即可，这里需要说下，在node-v13.4.0后的版本不支持win8.1以下的系统了。

- [官网下载](https://nodejs.org/download)
- [以前的版本下载](https://nodejs.org/dist/)

推荐淘宝的镜像库里下载

- [node.js mirror](https://npm.taobao.org/mirrors/node/)



> npm作为一个NodeJS的模块管理。我们要先配置npm的全局模块的存放路径以及cache的路径，例如我希望将以上两个文件夹放在NodeJS的主目录下，便在NodeJs安装目录下建立“node_global”及“node_cache”两个文件夹。                              　

　　在cmd命令行中使用如下命令：

```
npm config set prefix "D:\nodejs\node_global"
npm config set cache "D:\nodejs\node_cache"
```

https://www.cnblogs.com/doctorJoe/articles/4581672.html

由于国内的 npm 访问外网下载速度较慢，我们可以将 npm 源更换为淘宝的镜像（当然如果你觉得你的下载速度较快的话，也可以选择不进行更换），在 Git Bash 中输入以下指令



```
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```

**请注意如果进行了上述操作，那么之后的下载等操作需要使用到 npm 的地方你都应该更换为** `**cnpm**` **指令，这样才能起到加速作用，如果未进行更换，则使用** `**npm**` **即可。**



### 2、Git

[参考廖雪峰大神的 Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)



### 3、验证

```
git version
node -v
npm -v
```

## 安装Hexo

输入如下指令即可安装完成 Hexo 的安装，十分方便。



```
$ npm install hexo-cli -g
```

在安装过程中可能会出现`WARN`提示，这是因为 Hexo 的某些内容不支持 Windows 系统，我们无需理会 (程序员只关心 Error，不关心 Warning🙃)。

安装完成后，我们输入 `hexo -v` 命令，如果显示如下信息，则安装成功。



```
hexo-cli: 1.1.0
os: Windows_NT 10.0.17134 win32 x64
http_parser: 2.8.0
node: 10.14.1
v8: 6.8.275.32-node.36
uv: 1.23.2
...
```

底下还有许多包的版本信息，可以看到 Hexo 的依赖项还是比较多的。

### 初始化博客

在我们想要存放博客文件的盘下进入 Git Bash ，首先我们要新建一个文件夹用来存放我们写的博客和其它相关文件，在命令行中输入`mkdir Blog` 命令，便可新建一个名称为 Blog 的文件夹（文件夹名可自取）。接下来进入刚创建的文件夹，可使用 `cd Blog` 命令，或是进入该文件夹后在空白处单击右键，再点击 Git Bash Here （还是多练习以下命令行的简单命令为好）。

进入 Blog 文件夹后，输入 `hexo init` 命令，即可完成该文件夹的初始化，在此期间，Hexo 会自动克隆和创建一系列相关文件，在结束后为得到如下反馈：



```
$ hexo init
INFO  Cloning hexo-starter to F:\desktop\Blog
Cloning into 'F:\desktop\Blog'...
...
Unpacking objects: 100% (71/71), done.
Submodule 'themes/landscape' (https://github.com/hexojs/hexo-theme-landscape.git) registered for path 'themes/landscape'
Cloning into 'F:/desktop/Blog/themes/landscape'...
...
Receiving objects: 100% (890/890), 2.56 MiB | 362.00 KiB/s, done.
Resolving deltas: 100% (465/465), done.
Submodule path 'themes/landscape': checked out '73a23c51f8487cfcd7c6deec96ccc7543960d350'
INFO  Install dependencies
...
INFO  Start blogging with Hexo!
```

当看到 `Start blogging with Hexo` 就知道我们已经初始化成功了，Blog 文件夹中会创建如下文件：

初始化以后的文件夹如下

```
.
├── _config.yml # 网站的配置信息，您可以在此配置大部分的参数。 
├── package.json
├── scaffolds # 模版文件夹
├── source  # 资源文件夹，除 _posts 文件，其他以下划线_开头的文件或者文件夹不会被编译打包到public文件夹
|   ├── _drafts # 草稿文件
|   └── _posts # 文章Markdowm文件 
└── themes  # 主题文件夹
```

### 生成博客页面

在 \source\_posts\ 文件夹中就保存着我们写的所有博客，当前我们并没有写任何博客，但是 Hexo 为自动生成一个 hello-world.md 文件，我们可以以此为例，看看我们的博客网页是啥样啦。

在 Git Bash 中输入 `hexo g` 命令（是 `hexo generate` 的简写），等待 Hexo 自动生成网页，得到如下反馈则生成成功：



```
$ hexo g
INFO  Start processing
INFO  Files loaded in 192 ms
INFO  Generated: index.html
...
INFO  28 files generated in 459 ms
```

接下来我们需要开启开启本地服务器，输入 `hexo s` 命令（是 `hexo server` 的简写），输出



```
$ hexo s
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```

我们就知道了网页运行在 [http://localhost:4000](https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A4000) 上，我们在浏览器中输入该地址便能进入我们创建的博客网页啦。

### 美化博客页面

#### 下载主题

可以看到打开的博客页面就是 Hexo 默认的页面，所以并不是非常得好看，我们可以自行选择更换，在 GitHub 上搜索 Hexo 主题还是有非常多的项目的。我在这里选择了目前使用人数比较多的 Next 主题进行演示。Next 主题的 Github 地址是 [theme-next/hexotheme-next](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Ftheme-next%2Fhexo-theme-next)。回到我们存放博客文件的根目录，输入如下指令，将该仓库克隆到本地。



```
$ cd Blog
$ git clone https://github.com/theme-next/hexo-theme-next themes/next
```

这样我们就将 Next 主题克隆到 themes/next 文件夹下啦。

#### 更改配置文件

使用编辑器打开根目录下的 `_config.yml` 文件，这个文件保存的就是 Hexo 的诸多配置项，我们可以对其进行个性化修改。在文件中找到 `theme` 配置选项，如下所示：



```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: landscape
```

可以看到现在的主题是默认的 `landscape` ，我们将其改为 `next` 即可。



```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
```

再在 Git Bash 中依次输入下面三条指令（发布三连），**请注意所有的 hexo 指令都是在根目录下进行的，如果当前目录不是根目录，必须先切换到根目录再执行命令**：



```
$ hexo clean   #清除之前生成的网站文件
$ hexo g       #生成当前网站文件
$ hexo s       #开启服务器
```

**再次打开** [**http://localhost:4000**](https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A4000) **，我们就能看到更换主题后的网站了，非常便捷。**

### 遇到的问题

更换主题buttfly后，重新生成文件后，打开本地hexo出现错误提示

```
extends includes/layout.pug block content include ./includes/mixins/post-ui.pug #recent-posts.recent-posts +postUI include includes/pagination.pug
```

### 解决问题

参考：https://github.com/jerryc127/hexo-theme-butterfly/issues/4

#### blog目录安装jade

```
npm install hexo-renderer-jade --save
```

#### 在根目录重新安装npm

**在package添加****`"hexo-renderer-jade": "^0.5.0",`** **在根目录重新安装npm**

```
npm install
```

附上安装成功的package.json

```
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "build": "hexo generate",
    "clean": "hexo clean",
    "deploy": "hexo deploy",
    "server": "hexo server"
  },
  "hexo": {
    "version": "5.2.0"
  },
  "dependencies": {
    "hexo": "^5.0.0",
    "hexo-generator-archive": "^1.0.0",
    "hexo-generator-category": "^1.0.0",
    "hexo-generator-index": "^2.0.0",
    "hexo-generator-tag": "^1.0.0",
    "hexo-renderer-ejs": "^1.0.0",
    "hexo-renderer-jade": "^0.5.0",
    "hexo-renderer-marked": "^3.0.0",
    "hexo-renderer-stylus": "^2.0.0",
    "hexo-server": "^2.0.0"
  }
}
```

## 部署博客

在完成了上述步骤之后，我们就可以在自己的电脑上打开博客网页了，但是怎么才能让别人也能访问到我们的网页呢？这就需要我们部署我们的博客网站了。幸运的是，GitHub 能为我们免费提供这一服务，那就是 GitHub Page ，我们需要做的就是在 GitHub 上新建一个名为 `<username>.github.io` (在`<username>`处填入你的用户名） 的仓库即可。

### 修改配置文件

打开根目录下的 `_config.yml` 文件，找到 `deploy` 选项，如下所示：



```
deploy:
  type:
```

将其修改为



```
deploy:
  type: git
  repo: https://github.com/<username>/<username>.github.io.git
  branch: master
```

在其中的 `<username>` 处填入你的 GitHub 用户名即可。保存配置文件并退出。

### 安装部署Git插件

```
npm install hexo-deployer-git --save
```



接下来在 Git Bash 中输入下面三条指令（部署三连）：



```
$ hexo clean
$ hexo g
$ hexo d
```

至此，我们就已经完成了个人博客网站的部署，在浏览器中输入你的地址 ：`<username>.github.io` ，就能看到我们的个人网站啦！