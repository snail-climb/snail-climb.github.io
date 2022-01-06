# 基于ECS搭建云上博客

## 1. 安装Apache HTTP服务
> Apache是世界使用排名第一的Web服务器软件。它可以运行在几乎所有广泛使用的计算机平台上，由于其跨平台和安全性被广泛使用，是最流行的Web服务器端软件之一。

### 1.1 安装Apache服务及其扩展包
```bash
yum -y install httpd mod_ssl mod_perl mod_auth_mysql
```

### 1.2 启动Apache服务
```bash
systemctl start httpd.service
```

### 1.3 测试Apache服务是否安装并启动成功
> Apache默认监听80端口，所以只需在浏览器访问http://公网地址

## 2. 安装MariaDB数据库
> 由于使用Wordpress搭建云上博客，需要使用MySQL数据库存储数据，现在我们将安装MySQL的开源替代品MariaDB（MariaDB完全兼容MySQL），并创建博客数据库。 

### 2.1 安装MariaDB Server
```bash
yum install -y mariadb-server
```

### 2.2 启动MariaDB Server
```bash
systemctl start mariadb
```
> 注：可执行如下命令查看MariaDB Server运行状态
```bash
systemctl status mariadb
```

### 2.3 设置数据库初始密码
```bash
mysqladmin -u root -p password
```
> 由于是第一次设置密码，因此在出现Enter Password的时候直接回车，然后输入要设置的密码，并二次确认即可。
> 请记住设置的密码，接下来将用于数据库连接操作。
> 说明：密码不显示。

### 2.4 连接数据库
```bash
mysql -uroot -p
```
> 在出现Enter password提示符的时候，输入之前设置的密码，即可连接数据库。

### 2.5 创建数据库
> 登陆数据库后，为博客创建一个数据库，这里数据库名设置为wordpress（也可以采用其他喜欢的名字），执行如下命令创建wordpress数据库：
```bash
create database wordpress;
```
> 如果要查看所有数据库，可以输入如下命令：
```bash
show databases;
```

### 2.6 退出数据库
```bash
exit; 或者 quit;
```

## 3. 安装 PHP 语言环境
> WordPress是使用PHP语言开发的博客平台，用户可以在支持PHP和MySQL数据库的服务器上架设属于自己的网站。也可以把WordPress当作一个内容管理系统（CMS）来使用。

### 3.1 安装PHP环境
```bash
yum -y install php php-mysql gd php-gd gd-devel php-xml php-common php-mbstring php-ldap php-pear php-xmlrpc php-imap
```

### 3.2 创建PHP测试页面
```bash
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
```

### 3.3 重启Apache服务
```bash
systemctl restart httpd
```

### 3.4 测试PHP页面
> 访问http://公网地址/phpinfo.php

## 4. Wordpress安装和配置
> 现在已经搭建好了LAMP（Linux、Apache、MariaDB、PHP）环境，接下来开始安装和配置WordPress

### 4.1 安装wordpress
```bash
yum -y install wordpress
```

### 4.2 修改WordPress配置文件
1. 修改wp-config.php指向路径为绝对路径
```bash
# 进入/usr/share/wordpress目录。
cd /usr/share/wordpress
# 修改路径。
ln -snf /etc/wordpress/wp-config.php wp-config.php
# 查看修改后的目录结构。
ll
```
2. 移动wordpress到Apache根目录
```bash
# 在Apache的根目录/var/www/html下，创建一个wp-blog文件夹。
mkdir /var/www/html/wp-blog
mv * /var/www/html/wp-blog/
```
3. 修改wp-config.php配置文件。在执行命令前，请注意替换命令中的以下三个参数值
* database_name_here/value1/：value1为之前步骤中创建的数据库名称
* username_here/value2/：/value2/为数据库的用户名
* password_here/value3/：/value3/为数据库的登录密码
```bash
sed -i 's/database_name_here/wordpress/' /var/www/html/wp-blog/wp-config.php
sed -i 's/username_here/root/' /var/www/html/wp-blog/wp-config.php
sed -i 's/password_here/123456/' /var/www/html/wp-blog/wp-config.php
```
4. 查看配置文件信息是否修改成功
```bash
cat -n /var/www/html/wp-blog/wp-config.php
```

### 4.3 重启Apache服务，执行如下命令：
```bash
systemctl restart httpd
```

### 4.4 测试Wordpress
1. 打开浏览器并访问 http://公网IP/wp-blog/wp-admin/install.php
2. 根据以下信息完成wordpress初始化配置，然后点击Install WordPress按钮完成Wordpress初始化
3. 单击Log In进行登录，输入上一步设置的用户名和密码
4. 登陆成功，就可以添加博客进行发布了

