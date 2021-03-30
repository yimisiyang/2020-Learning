## 1安装准备

**平台：**CentOS7、MySQL5.7（mysql5.6会有问题）、web server NGINX、zabbix5.0。

## 2平台安装

### 2.1 rpm安装zabbix资料库

```shell
# rpm -Uvh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-release-5.0-1.el7.noarch.rpm
# yum clean all
```

### 2.2 安装zabbix服务端和客户端

```shell
# yum install zabbix-server-mysql zabbix-agent
```

### 2.3 安装zabbix前端

获取软件源

```shell
# yum install centos-release-scl
```

编辑文件 `/etc/yum.repos.d/zabbix.repo`开启zabbix前端存储库

```shell
[zabbix-frontend]
...
enabled=1
...
```

yum安装zabbix前端包

```shell
# yum install zabbix-web-mysql-scl zabbix-nginx-conf-scl
```

### 2.4 安装并初始化MySQL5.7数据库

从官网获取MySQL安装包

https://dev.mysql.com/downloads/mysql/5.7.html

rpm方式安装MySQL5.7(按照下面安装下载所需的MySQL rpm包)

```shell
rpm -ivh mysql-community-common-5.7.31-1.el7.x86_64.rpm 
rpm -ivh mysql-community-libs-5.7.31-1.el7.x86_64.rpm 
rpm -ivh mysql-community-client-5.7.31-1.el7.x86_64.rpm 
rpm -ivh mysql-community-server-5.7.31-1.el7.x86_64.rpm 
rpm -ivh mysql-community-libs-compat-5.7.31-1.el7.x86_64.rpm
```

初始化数据库

```shell
#查看MySQL服务是否启动
systemctl status mysqld #查看状态
systemctl start mysqld #启动
systemctl stop mysqld  #停止
systemctl restart mysqld #重启
#首次登陆不需要密码
mysql -uroot 
#使用数据库(以下命令在数据库执行)
use mysql
#更新密码
update user set password=password('你要设的密码') where user='root';
#授权远程登陆
GRANT ALL PRIVILEGES ON *.* TO root@"%" IDENTIFIED BY "远程登陆密码";　
#退出数据库
quit;
```

数据库中创建zabbix用户

```
# mysql -uroot -p
password
mysql> create database zabbix character set utf8 collate utf8_bin;
mysql> create user zabbix@localhost identified by 'password';
mysql> grant all privileges on zabbix.* to zabbix@localhost;
mysql> quit;
```

导入zabbix服务端初始化表和数据，这里数据库密码为自己设置的。

```shell
# zcat /usr/share/doc/zabbix-server-mysql*/create.sql.gz | mysql -uzabbix -p [password]
```

### 2.5 为zabbix服务端配置数据库

配置文件 `/etc/zabbix/zabbix_server.conf`

```
DBPassword=password  #password自己设置
```

### 2.6 为zabbix配置php前端

配置文件 ` /etc/opt/rh/rh-nginx116/nginx/conf.d/zabbix.conf`，取消这两行注释，并将server_name配置成IP或名字（我这里配置成了IP）

```
# listen 80;
# server_name example.com;
```

编辑配置文件 ` /etc/opt/rh/rh-php72/php-fpm.d/zabbix.conf` 将nginx添加到listen.acl_users

```
listen.acl_users = apache,nginx
```

更改时区，同样是` /etc/opt/rh/rh-php72/php-fpm.d/zabbix.conf`文件

```
; php_value[date.timezone] = Asia/Shanghai
```

### 2.7 开启zabbix服务器和客户端进程，并设置开机自启

```shell
# systemctl restart zabbix-server zabbix-agent rh-nginx116-nginx rh-php72-php-fpm
# systemctl enable zabbix-server zabbix-agent rh-nginx116-nginx rh-php72-php-fpm
```

### 2.8 配置zabbix前端

```
http://ip地址
```

用户名：`Admin`;密码：`zabbix`

## 3.使用zabbix

### 3.1添加用户

- 转到 管理->用户界面，添加用户：zabbix;密码：root@123
- 在用户组中设置权限

### 3.2 添加主机

**注意：**你想要监控的主机在zabbix中必须是联网的（包括物理机，虚拟机），监控的机器可以是网络交换器，虚拟机或者一些应用。

- 在要监控的主机中安装客户端并进行配置。

- 在配置->主机中

