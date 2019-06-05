---
title: 使用Hexo搭建个人博客02 -- 部署上线篇
date: 2019-06-05 15:37:02
tags: Hexo
categories:
- 技术
- 博客
---
是一种用来消息聚合的格式规范
<!--more-->

#  部署Hexo
我们写 blog 更多还是想一起分享的，本地自嗨怎么能行，肯定要部署到服务器上啦~
目前有2种方式可以部署我们的博客 
-  使用 github 或  coding 的 page 服务
-  部署在自己的VPS上

##  github部署

打开  [github](https://github.com) ，新建一个 repository， Repository name 一定要为 **[你的用户名]**.github.io

将你的本地公钥绑定在github上，如果尚未生成 ssh 公钥对，执行如下命令生成新的公钥对：

```shell
$ ssh-keygen
```
如果是 Windows 操作系统，此时会在 C:\Users\Username\.ssh\ 目录下生成密钥文件 id_rsa 和公钥文件 id_rsa.pub。

在 github 右上角头像点击 settings /  SSH and  GPG keys ，新建一个 SSH key ，将你id_rsa.pub 文件中的内容复制到 key中

![new SHH key](/images/hexo-init/hexo2.jpg)

在站点配置文件 _config.yml 中设置
``` yaml  _config.yml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo:
        github: [github仓库地址]git@github.com:lanme2019/lanme2019.github.io.git
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

## VPS部署
**环境准备**
`git`
`nginx`

使用 VPS 部署博客的主要思路分为三步：

- hexo deploy 的时候通过 git 把 public 目录下的博客静态资源推送到远程仓库中
- 推送更新时触发 Git Hooks 将静态资源克隆到网站根目录下
- 使用 nginx 作为 Web 服务器提供对博客的 HTTP 访问

### 远程仓库推送
在本地 Git Bash 中执行如下命令将 ssh 公钥上传到 VPS：
```shell
$ ssh-copy-id [用户]root@[你的服务器地址]luanmingyi.cn  
```
{% note info %}
该命令会自动把默认 ssh 公钥 id_rsa.pub 中的内容拷贝到 root 用户目录下的 .ssh/authorized_keys 文件中。
{% endnote %}
此时在本地 cmd 中用 root 用户登陆 VPS 将会直接成功登陆而无须输入密码：
```shell
$ ssh root@luanmingyi.cn
```
在 root 用户目录下执行如下命令创建远程仓库：
```shell
$ mkdir blog.lanme2019.git
$ cd blog.lanme2019.git
$ git init --bare

```
在本地站点配置文件 _config.yml 中添加 git 远程仓库信息：
```yaml
deploy:
  type: git
  repo:
        repo: root@luanmingyi.cn:~/blog.lanme2019.git
  branch: master
```
使用`hexo deploy` 命令部署
配置git-hocks  推送代码自动更新
将克隆的代码复制到nginx目录下
配置nginx.conf 文件 
```shell
sbin  bin 目录下
./nginx -s reload 重启
./nginx -s stop  停止
./nginx   启动
```

#  CDN 加速
我的博客使用又拍云CDN服务  加入又拍云联盟  免费使用CDN流量


#   项目主题托管
hexo 的 deploy  只能部署静态资源到 git 仓库  如果我们的主题文件需要备份怎么办?

- 在github上新建分支  如 sagiri
- 在本地项目目录下  
```shell
git remote add origin git@github.com:lanme2019/lanme.git
git push -u origin sagiri
```





