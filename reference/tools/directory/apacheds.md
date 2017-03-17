# 安装
```
# 使用二进制包安装
> sh apacheds-*.bin
...
# 许可认证
Do you agree to the above license terms? [yes or no]
> yes
# 安装路径
Where do you want to install ApacheDS? [Default: /opt/apacheds-2.0.0-M23]
# 实例路径
Where do you want to install ApacheDS instances? [Default: /var/lib/apacheds-2.0.0-M23]
# 实例名称
What name do you want for the default instance? [Default: default]
> gsafety.com
# 启动脚本
Where do you want to install the startup script? [Default: /etc/init.d]
# 运行用户
Which user do you want to run the server with (if not already existing, the specified user will be created)? [Default: apacheds]
# 运行组
Which group do you want to run the server with (if not already existing, the specified group will be created)? [Default: apacheds]

Installing...
Done.
ApacheDS has been installed successfully.

# 启动
> /etc/init.d/apacheds-2.0.0-M23-gsafety.com start
Starting ApacheDS - gsafety.com...
```

# 配置
- 管理员密码 ```uid=admin,ou=system``` 中修改 ```userPassword```
- 配置密码策略
  ```
  ou=config
    ads-directoryServiceId=<default>
        ou=interceptors
            ads-interceptorId=authenticationInterceptor
                ou=passwordPolicies
  ```
  中修改 ```ads-pwdminlength```
- 配置Partitions
  ```
  ou=config
    ads-directoryServiceId=<default>
      ou=partitions
  ```
