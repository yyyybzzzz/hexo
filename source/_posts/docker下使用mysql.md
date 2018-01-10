---
title: docker下使用mysql
date: 2018-01-08 22:03:01
tags:
    - docker
---
>开发过程中经常需要安装、调试mysql数据库，还需要在各种操作系上安装包依赖，实在是繁琐，因此就研究了一下如何在docker上运行一个mysql镜像，省却了我安装、找依赖的问题。本次安装采用的是拉取镜像的方式

### 一、从公共仓库拉取镜像

```bash
docker pull registry.docker-cn.com/library/mysql:5.7
```

### 二、获得官方的docker-entrypoint.sh文件

根据不同的版本下载不同的docker-entrypoint.sh文件，我这里使用的mysql5.7，所以下载的是5.7对应的版本  


[docker-entrypoint.sh文件获取地址](https://github.com/docker-library/mysql)

将文件复制到本地之后，还要把文件放入到`/usr/local/bin/`中 (只针对macos)，接下来就可以创建容器了。


### 三、创建容器
在创建容器之前创建三个文件夹`data cnf logs` 。

```bash
mkdir -p /mysql/data /mysql/cnf /mysql/logs
```
data目录将映射为mysql容器配置的数据文件存放路径 
logs目录将映射为mysql容器的日志目录 
conf目录里的配置文件将映射为mysql容器的配置文件

```bash
docker run -p 3306:3306 --name mysql -v /mysql/data:/var/lib/mysql -v /mysql/cnf:/etc/mysql/cnf.d -v /mysql/logs:/etc.log/mysql/log -e MYSQL_ROOT_PASSWORD=135256 -d registry.docker-cn.com/library/mysql:5.7
```