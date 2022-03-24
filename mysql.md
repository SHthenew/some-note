# Mysql for Server

## 服务器端安装mysql

### 1. 安装mysql

`sudo apt-get install mysql-server`

### 2. 保护mysql

> MySQL服务器软件包附带一个名为mysql_secure_installation的脚本，该脚本可以执行一些与安全性相关的操作。<br>

执行命令 `sudo mysql_secure_installation`

* 系统将要求您配置VALIDATE PASSWORD PLUGIN，该工具用于测试MySQL用户密码的强度并提高安全性。<br>
* 密码验证策略分为三个级别：低，中和强。如果您不想设置验证密码插件，请按ENTER。
* 在下一个提示符下，将要求您为MySQL根用户设置密码。
* 完成该操作后，脚本还将要求您删除匿名用户，限制root用户对本地计算机的访问并删除测试数据库。您应该对所有问题回答“是”。

### 3. 设置外部访问

键入`mysql`进入数据库控制台

#### 3.1 创建角色与赋权

```mysql
# 进入mysql库
use mysql;

# 密码必须与步骤2所设置的密码强度等级相匹配
create user 'your_user'@'%' identified by 'your_password';

# 给当先实例中所有的数据库和表赋予所有的权限，并赋予其赋权权限
# *.* 表示所有的数据库和表，可用mysql.user形式指定数据表
# % 表示可以从任意远程主机登录，localhost表示本地，
# with grant option 表示给该用户附带授权权限
grant all privileges on *.* to 'your_user'@'%' with grant option;

# 刷新权限
flush privileges; 
```

#### 3.2 配置远程连接

键入`quit`退出mysql控制台 <br>
打开文件 `vim /etc/mysql/mysql.conf.d/mysqld.cnf` <br>
注释行 `bind-address = 127.0.0.1`，表示删除绑定本地地址（可设置连接数据库的IP限制，IP用空格隔开）

#### 3.3 重启mysql服务

重启服务 `service mysql restart` <br>
停止服务 `service mysql stop` <br>
启动服务 `service mysql start` <br>
