# 安装
## Centos7
先移除mariadb ```rpm -e --nodeps mariadb-libs```
### rpm包
- common
- libs
- client
- server

### 初始化
- 创建配置文件(如果不存在)
```
cp /usr/share/mysql/my-default.cnf /etc/my.cnf
```

- 初始化
```
# /etc/my.cnf中datadir下清空(rm -rf *)

mysqld --initialize

chown -R mysql:mysql DATADIR
systemctl start mysqld
```

- 初次登陆
```
# 密码在/var/log/mysqld.log中
grep "A temporary password" /var/log/mysqld.log

# 在/etc/my.conf中关闭密码策略
validate_password = off

mysql -u root -p

```

- 修改初始密码
```
mysqladmin -u root -p password
```

- 状态变更
```
# el6
service mysqld start/stop/restart/--help
# el7
systemctl start/stop/restart/reload/status mysqld
```
- 重置Root
    ```
    # 先把运行着的Mysql杀掉
    service mysqld stop
    # 跳过授权
    mysqld_safe --skip-grant-tables&
    # 登录
    mysql -u root mysql

    # 旧版
    use mysql;
    update user set password=password("******") where user="root";
    flush privileges;

    # 新版
    USE mysql;
    UDPATE mysql.user SET authentication_string=password("******") WHERE user='root' AND host='localhost';
    flush privileges;

    # 恢复安全
    mysqld_safe &

    # 延期账户
    SET PASSWORD = PASSWORD('your new password');
    ALTER USER 'root'@'localhost' PASSWORD EXPIRE NEVER;
    flush privileges;
    ```

- 故障排查
    - mysql权限导致无法启动
        - 报错
        ```
        # /var/log/mysqld.log
        [ERROR] InnoDB: Plugin initialization aborted with error Generic error
        ```
        - 修复
        ```
        # /var/lib
        chown mysql:mysql -R /var/lib/mysql
        ```
- 创建账号

    ```
    CREATE DATABASE 库 CHARACTER SET utf8 COLLATE utf8_bin;
    GRANT all on 库.* to '账号'@'访问地址' identified by '密码';
    flush privileges;
    # localhost为本地访问，%为任意地址访问
    ```
