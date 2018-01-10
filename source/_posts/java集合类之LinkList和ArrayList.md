---
title: java集合类之LinkList和ArrayList
date: 2017-06-10 11:18:19
tags:
    -java基础
    -java集合类
---
> 最近感觉自己的java基础有点差，所以打算过一遍java基础，就从java集合类开始吧。本篇文章主要回顾一下`LinkList`和`ArrayList`  


### 一、LinkList
LinkList实现了 `java.util.List` `Cloneable` `java.io.Serializable` 接口
LinkList是线程不安全的，如果要在多线程的情况下调用，可以使用Collections类中的静态方法SynchronizedList()
