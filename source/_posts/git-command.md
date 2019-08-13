---
title:  git 命令
date: 2019-06-24 8:00:00
tags:  git 
categories:
- 学习笔记
---
# 常用GIT命令汇总
<!--more-->

## 本地仓库第一次提交到远程仓库
1.初始化本地仓库
```shell
git init
```
2.将本地仓库文件  交由 `git`管理
```shell
git add .
```
3.提交代码到本地区
```shell
git  commit  -m  "init"
```
4.添加远程仓库地址
```shell
git remote add  origin  [git仓库地址]
```
5.`push` 代码到远程仓库
```shell
git push origin master
```
tips.`pull` 远程仓库代码 保持版本一致
** --allow-unrelated-histories  //将本地代码仓库和远程库  历史提交记录合并 **
```shell
git pull origin master --allow-unrelated-histories
```
```
git pull  =   git fetch  +  git  merge
```

## 配置了 .gitignore 不生效
当我们将 `.gitignore` 文件配置好后，却往往不能失效。这是因为 `.gitignore` 只能忽略那些没有被追踪(`track`)的文件，因为 `git`存在本地缓存，如果文件已经纳入了版本管理，那么修改 `.gitignore` 是不能失效的。那么解决方案就是要将 `git` 的本地缓存删除，然后重新提交。
 
1. 清除本地缓存
```shell script
git rm -r --cached .
```
2. 配置 `.gitignore` 文件
3. 重新将文件交给`git`管理
```shell script
git add .
```



