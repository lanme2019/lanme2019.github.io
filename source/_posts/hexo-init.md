---
title: 使用Hexo搭建个人博客01 -- 基础建站篇
date: 2019-06-05 8:00:00
tags: Hexo 
categories:
- 灵魂向导

---
是一种用来消息聚合的格式规范
<!--more-->
# 环境准备
- [Node.js](<https://nodejs.org/zh-cn/>)  (6.9版本及以上)
- [git](<https://git-scm.com/>) 

{% note info %}
 Hexo 依赖于 Node.js 和 git，所以在安装 Hexo 之前先确保已安装了这两项应用。
{% endnote %}

具体安装方法自行google啦~

# 开始使用

##  安装 yarn

在 `cmd` 下输入

```shell
$ npm install -g  yarn
```
{% note info %}

`-g`  表示全局安装    将插件加入系统环境变量中   使 `cmd`  可以在任意目录下使用 `yarn` 指令

{% endnote %}

##  安装 Hexo

```bash
$ yarn add  hexo 
```
## 初始化Hexo
安装 Hexo 完成后，执行下列命令，Hexo 将会在您指定文件夹中新建所需要的文件。
```shell
$ hexo init <folder>
$ cd <folder>
$ yarn
```
执行完毕后，你的项目会生成以下目录结构
```plain
.
├── node_modules       //依赖安装目录
├── scaffolds          //模板文件夹，新建的文章将会从此目录下的文件中继承格式
|   ├── draft.md         //草稿模板
|   ├── page.md          //页面模板
|   └── post.md          //文章模板
├── source             //资源文件夹，用于放置图片、数据、文章等资源
|   └── _posts           //文章目录
├── themes             //主题文件夹
|   └── landscape        //默认主题
├── .gitignore         //指定不纳入git版本控制的文件
├── _config.yml        //站点配置文件
├── db.json            
├── package.json
└── yarn-lock.json
```
到这里你就完成了所有的准备工作，只需一条指令即可启动你的博客
##  本地预览Hexo
项目目录下依次输入  
```shell
$ hexo cl       #  清除本地静态资源和db.json文件
$ hexo g        #  生成静态资源 用来部署项目
$ hexo s        #  启动本地预览服务器  默认端口4000
```
成功后，访问 http://localhost:4000/  启动你的预览

![hexo 预览](/images/hexo-init/hexo1.png)

{% note info %}
如果端口被占用想自定义一个新端口  再或者想启动Debug模式怎么办？
hexo  s启动命令也有附加参数
--p [端口号]  修改端口号 
--debug   开启debug模式
{% endnote %}

```shell
$ hexo s  --p  [端口号]   --debug
```

##  部署Hexo
我们写 blog 更多还是想一起分享的，本地自嗨怎么能行，肯定要部署到服务器上啦~
目前有2种方式可以部署我们的博客 
-  使用 github 或  coding 的 pages 服务
-  部署在自己的VPS上
###  github部署

打开  [github](https://github.com) ，新建一个 repository 
Repository name 一定要为 **[你的用户名]**.github.io
将你的本地公钥绑定在github上，如果尚未生成 ssh 公钥对，执行如下命令生成新的公钥对：

```shell
$ ssh-keygen
```
如果是 Windows 操作系统，
此时会在 C:\Users\Username\.ssh\ 目录下生成密钥文件 id_rsa 和公钥文件 id_rsa.pub。

在 github 右上角头像点击 settings /  SSH and  GPG keys ，
新建一个 SSH key ，将你id_rsa.pub 文件中的内容复制到 key中

![new SHH key](/images/hexo-init/hexo2.jpg)

在站点配置文件 _config.yml 中设置
``` yaml  _config.yml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo:
        github: [你的github仓库地址]
  branch: master
```
安装Hexo部署插件
```shell
$ yarn  add  hexo-deployer-git
```

在当前目录下打开 cmd输入以下命令 开始部署					 
```shell
$ hexo cl
$ hexo g
$ hexo d
```
访问  [你的github项目名].github.io   查看是否部署成功

{% note info %}
每次启动或者部署输入三个指令很麻烦，可以把这三个指令写入到 `package.json` 中
{% endnote %}
```yaml
 "scripts": {
    "deploy": "hexo clean && hexo g -d",
    "start": "hexo clean && hexo g && hexo s --debug",
  }
```
以后只需输入  `yarn  start` ( 启动预览 )  ` yarn  deploy` ( 部署 )  

### VPS部署

考虑考虑



解开了揭开


