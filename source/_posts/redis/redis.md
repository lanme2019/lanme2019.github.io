---
title: redis笔记
date: 2019-06-05 8:00:00
tags: redis
categories:
- 面试
---

# redis 笔记
<!--more-->
- 单线程 
- 非阻塞IO(NIO)
- 多种数据结构 字符串 hash  list  linked 位图  Hyperloglogs 
- 禁止使用复杂度为 O（n）的命令 大量占用线程资源

## 关于key的注意事项
- 不要使用过长的KEY  
- 不要因为过短缺少可读性 
- 最好使用统一的规范来设计 Key，比如”object-type:id:attr”，以这一规范设计出的 Key 可能是”user:1000″或”comment:1234:reply-to”
- 最大key长 512M  (超過1024字节就不好了)

