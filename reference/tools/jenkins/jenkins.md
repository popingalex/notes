```xml
<!-- $TOMCAT_HOME/conf/server.xml -->
<Connector port="8080" URIEncoding="UTF-8"/>
```

```xml
<!-- $JENKINS_HOME/config.xml -->
<hudson>
  <useSecurity>true/false</useSecurity>
  ...
</hudson>
```

# 插件

# slave
```
useradd jenkins_slave -d /home/jenkins_slave -p slave123
```

- 切换到 ```jenkins_slave``` 用户下
- 生成密钥 ```ssh-keygen```
- 复制密钥 ```cat /home/jenkins_slave/.ssh/id_rsa.pub > authorized_keys``` ```chmod 700 authorized_keys``` 这步好像没啥用
- 复制私钥 ```id_rsa``` 到Master
- 路径最好写完整的绝对路径
