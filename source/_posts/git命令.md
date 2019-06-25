---
title:  git 命令
date: 2019-06-24 8:00:00
tags:  git 
categories:
- 开发
---
# 常用GIT命令汇总
<!--more-->

#### 本地仓库第一次提交到远程仓库
1.初始化本地仓库
```shell
git init
```
2.添加远程仓库地址

```shell
git remote add  origin  [git仓库地址]
```
3.将本地仓库文件  交由 git 管理
```shell
git add .
```
4.提交代码到本地区
```shell
git  commit  -m  "init"
```
5.pull 远程仓库代码 保持版本一致
** --allow-unrelated-histories  //将本地代码仓库和远程库  历史提交记录合并 **

```shell
git pull origin master --allow-unrelated-histories
```
6.push 代码到远程仓库
```shell
git push origin master
```

```
git pull  =   git fetch  +  git  merge
```



