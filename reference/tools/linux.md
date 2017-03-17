### 用户管理

```shell
# 用户创建
useradd LOGIN
-m 创建home
-d 指定HOME_DIR
-p 指定密码

# 用户修改
usermod LOGIN
-d 指定HOME_DIR
-m 迁移home

# 用户删除
userdel LOGIN
-r 移除home

# 用户密码
passwd LOGIN
```

### 压缩打包

```shell
# tar
tar [Option...] FILE
-c 打包
-f use archive file
-x 从archive中解压
-z gzip
-j bzip
-v 文件列表

-C 目标目录
# zip
unzip [-Z] [-opts] FILE [-d 目标目录]
-Z zipinfo
-v 文件列表
```

### 环境变量

```shell
export NAME=VALUE
```

### 网络状况
- 查看端口占用
  ```shell
  netstat -tunlp | grep
  ```

  ```shell
  lsof -i:端口号
  ```

- 排查地址解析(可能导致网络慢)
  ```
  # /etc/sysconfig/network-scripts/ifcfg-eth0
  DNS1="实际使用的DNS"

  systemctl restart network
  ```

### 代理配置
```shell
export http_proxy='http://host:port/'
```

### 系统资源
```
df -lh
df -lT
```

```
/proc/cpuinfo/
```

### 包管理
- 查看
```
rpm -qa | grep -i mysql
```

- 删除
```
rpm -e --nodeps [package]
```

- 安装
```
rpm -ivh *.rpm
```

- 升级(同时升级, 防止冲突)
```
rpm -Uvh *.rpm *.rpm *.rpm ...
```

### 文件查找
- 查找可执行文件
```
whereis xxx
```
- 查找文件
```
find [位置] -name '文件名'
```
