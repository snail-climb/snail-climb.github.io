# 快速搭建LAMP环境

## 1. LAMP环境介绍

### 1.1 云服务器ECS
> 云服务器（Elastic Compute Service，简称ECS）是阿里云提供的性能卓越、稳定可靠、弹性扩展的IaaS（Infrastructure as a  Service）级别云计算服务。云服务器ECS免去了您采购IT硬件的前期准备，让您像使用水、电、天然气等公共资源一样便捷、高效地使用服务器，实现计算资源的即开即用和弹性伸缩。阿里云ECS持续提供创新型服务器，解决多种业务需求，助力您的业务发展。

### 1.2 Linux
> Linux是一套免费使用和自由传播的类Unix操作系统，是一个基于POSIX和Unix的多用户、多任务、支持多线程和多CPU的操作系统。
> Linux能运行主要的 UNIX 工具软件、应用程序和网络协议。它支持 32 位和 64 位硬件。
> Linux 继承了 Unix 以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。

### 1.3 Apache
> Apache HTTP Server（简称Apache），是Apache软件基金会的一个开放源代码的网页服务器，可以在大多数电脑操作系统中运行，由于其具有的跨平台性和安全性，被广泛使用，是最流行的Web服务器端软件之一。

### 1.4 MySQL
> MySQL 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

### 1.5 PHP
> PHP（PHP：Hypertext Preprocessor递归缩写）中文名字是：“超文本预处理器”，是一种广泛使用的通用开源脚本语言，适合于Web网站开发，它可以嵌入HTML中。编程范型是面向对象、命令式编程的。

## 2. 安装Apache HTTP服务
> Apache是世界使用排名第一的Web服务器软件。它可以运行在几乎所有广泛使用的计算机平台上，由于其跨平台和安全性被广泛使用，是最流行的Web服务器端软件之一。

### 2.1 安装Apache服务及其扩展包
```bash
yum -y install httpd httpd-manual mod_ssl mod_perl mod_auth_mysql
```

### 2.2 启动Apache服务
```bash
systemctl start httpd.service
```

### 2.3 测试Apache服务是否安装并启动成功
> Apache默认监听80端口，所以只需在浏览器访问http://公网地址

## 3. 安装并配置MySQL
> MySQL是最流行的关系型数据库管理系统，在WEB应用方面MySQL是最好的 RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

### 3.1 从官方的Yum Repository下载并安装MySQL
```bash
rpm -e mariadb-libs --nodeps
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-common-5.7.35-1.el7.x86_64.rpm
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-libs-5.7.35-1.el7.x86_64.rpm
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-libs-compat-5.7.35-1.el7.x86_64.rpm
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-client-5.7.35-1.el7.x86_64.rpm
yum install -y https://mirrors.aliyun.com/mysql/MySQL-5.7/mysql-community-server-5.7.35-1.el7.x86_64.rpm
```

### 3.2 查看MySQL版本号
```bash
mysql -V
```

### 3.3 启动 MySQL 数据库
```bash
systemctl start mysqld.service
```

### 3.4 查看MySQL初始密码
```bash
grep "password" /var/log/mysqld.log
```

### 3.5 登录数据库
```bash
mysql -uroot -p
```

### 3.6 修改MySQL默认密码
```bash
# 修改密码安全策略为低（只校验密码长度，至少8位）
set global validate_password_policy=0;  
ALTER USER 'root'@'localhost' IDENTIFIED BY '12345678';
```

### 3.7 授予root用户远程管理权限
```bash
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '12345678';
```

### 3.8 输入exit 或 quit退出数据库

## 4. 安装PHP
> PHP（PHP：Hypertext Preprocessor递归缩写）中文名字是：“超文本预处理器”，是一种广泛使用的通用开源脚本语言，适合于Web网站开发，它可以嵌入HTML中。编程范型是面向对象、命令式编程的。

### 4.1 安装PHP环境
```bash
yum -y install php php-mysql gd php-gd gd-devel php-xml php-common php-mbstring php-ldap php-pear php-xmlrpc php-imap
```

### 4.2 创建PHP测试页面
```bash
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
```

### 4.3 重启Apache服务
```bash
systemctl restart httpd
```

### 4.4 测试PHP页面
> 访问http://公网地址/phpinfo.php

## 5. 安装phpMyAdmin
> phpMyAdmin是一个MySQL数据库管理工具，通过Web接口管理数据库方便快捷。

### 5.1 创建phpMyAdmin数据存放目录
```bash
mkdir -p /var/www/html/phpmyadmin
```

### 5.2 下载phpMyAdmin压缩包
```bash
wget --no-check-certificate https://files.phpmyadmin.net/phpMyAdmin/4.0.10.20/phpMyAdmin-4.0.10.20-all-languages.zip
```

### 5.3 安装unzip并解压phpMyAdmin压缩包
```bash
yum install -y unzip
unzip phpMyAdmin-4.0.10.20-all-languages.zip
```

### 5.4 复制phpMyAdmin文件到数据存放目录
```bash
mv phpMyAdmin-4.0.10.20-all-languages/*  /var/www/html/phpmyadmin
```

### 5.5 在本地浏览器的址栏中，输入http://公网IP/phpmyadmin，访问phpMyAdmin

### 5.6 在phpMyAdmin登录页面，依次输入MySQL的用户名和密码进行登录

