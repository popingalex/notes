# 安装
```
> sh atlassian-jira-software-7.3.0-x64.bin
Unpacking JRE ...
Starting Installer ...
Jan 22, 2017 7:36:42 PM java.util.prefs.FileSystemPreferences$1 run
INFO: Created user preferences directory.
Jan 22, 2017 7:36:42 PM java.util.prefs.FileSystemPreferences$2 run
INFO: Created system preferences directory in java.home.

This will install JIRA Software 7.3.0 on your computer.
OK [o, Enter], Cancel [c]

# 安装类型
Choose the appropriate installation or upgrade option.
Please choose one of the following:
Express Install (use default settings) [1], Custom Install (recommended for advanced users) [2, Enter], Upgrade an existing JIRA installation [3]
> 2

# 安装位置
Where should JIRA Software be installed?
[/opt/atlassian/jira]

# 数据位置
Default location for JIRA Software data
[/var/atlassian/application-data/jira]

# 端口配置
Configure which ports JIRA Software will use.
JIRA requires two TCP ports that are not being used by any other
applications on this machine. The HTTP port is where you will access JIRA
through your browser. The Control port is used to startup and shutdown JIRA.
Use default ports (HTTP: 8080, Control: 8005) - Recommended [1, Enter], Set custom value for HTTP and Control ports [2]

# 服务配置
JIRA can be run in the background.
You may choose to run JIRA as a service, which means it will start
automatically whenever the computer restarts.
Install JIRA as Service?
Yes [y, Enter], No [n]

Details on where JIRA Software will be installed and the settings that will be used.
Installation Directory: /opt/atlassian/jira
Home Directory: /var/atlassian/application-data/jira
HTTP Port: 8080
RMI Port: 8005
Install as service: Yes
Install [i, Enter], Exit [e]
```

# 开关
- 启动 ```sh /opt/atlassian/jira/bin/start-jira.sh```
- 关闭 ```sh /opt/atlassian/jira/bin/stop-jira.sh```

# 替换
在 ```/opt/atlassian/jira/atlassian-jira/WEB-INF/lib``` 添加：
- ```atlassian-extras-*.jar```
- ```mysql-connector-java-*-bin.jar```

# 配置
## General Configuration
### Settings
#### BASE URL
若修改path，如 ```http://192.168.0.1:8080/jira``` , 需要改 ```${jira_home}/conf/server.xml``` 中 ```<Context/>``` 中 ```path="/jira"```

### Advanced Settings
- jira.date.picker.java.format
  变更 ```d/MMM/yy``` 为 ```yyyy/MM/dd```
- jira.date.picker.javascript.format
  变更 ```%e%b%y``` 为 ```%Y/%m/%d```
- jira.date.time.picker.java.format
  变更 ```dd/MMM/yy h:mm a``` 为 ```yyyy/MM/dd HH:mm```
- jira.date.time.picker.javascript.format
  变更 ```%e/%b/%y %I:%M %p``` 为 ```%Y/%m/%d %H:%M```
- jira.projectkey.pattern
  变更 ```([A-Z][A-Z0-9]+)``` 为 ```([A-Z][A-Z_0-9]+)```

### Advanced JIRA application configuration
#### ```jira-config.properties```
- 文件位置

  ```
  # 文件不存在则创建
  # from installer
  C:\Program Files\Atlassian\Application Data\JIRA (on Windows)
  /var/atlassian/application-data/jira (on Linux)
  # from archive
  C:\jira\home (on Windows)
  /var/jira-home (on Linux or Solaris)
  ```
- 属性来源

  参考 ```/opt/atlassian/jira/atlassian-jira/WEB-INF/classes/jpm.xml```
- 配置内容

  ```properties
  # 相对时间
  jira.lf.date.relativize = false
  # 管理员session
  jira.websudo.is.disabled = true
  ```

# 备份还原
- 将归档文件放到 ```import``` 下导入
- 手动复制 ```data``` 下的 ```attachments``` 与 ```avatars```

# 插件
- 工作流工具组 ```jira-suite-utilities```
- 中文
