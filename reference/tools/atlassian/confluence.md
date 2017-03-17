# 安装
```
> sh atlassian-confluence-6.0.3-x64.bin
Unpacking JRE ...
Starting Installer ...
Jan 24, 2017 9:47:58 AM java.util.prefs.FileSystemPreferences$2 run
INFO: Created system preferences directory in java.home.

This will install Confluence 6.0.3 on your computer.
OK [o, Enter], Cancel [c]

# 安装类型
Choose the appropriate installation or upgrade option.
Please choose one of the following:
Express Install (uses default settings) [1],
Custom Install (recommended for advanced users) [2, Enter],
Upgrade an existing Confluence installation [3]
> 2

# 安装位置
Where should Confluence 6.0.3 be installed?
[/opt/atlassian/confluence]

# 数据位置
Default location for Confluence data
[/var/atlassian/application-data/confluence]

# 端口配置
Configure which ports Confluence will use.
Confluence requires two TCP ports that are not being used by any other
applications on this machine. The HTTP port is where you will access
Confluence through your browser. The Control port is used to Startup and
Shutdown Confluence.
Use default ports (HTTP: 8090, Control: 8000) - Recommended [1, Enter], Set custom value for HTTP and Control ports [2]

# 服务配置
Confluence can be run in the background.
You may choose to run Confluence as a service, which means it will start
automatically whenever the computer restarts.
Install Confluence as Service?
Yes [y, Enter], No [n]

Extracting files ...

Please wait a few moments while we configure Confluence.
Installation of Confluence 6.0.3 is complete
Start Confluence now?
Yes [y, Enter], No [n]
```

# 开关
- 启动 ```sh /opt/atlassian/confluence/bin/start-confluence.sh```
- 关闭 ```sh /opt/atlassian/confluence/bin/stop-confluence.sh```

# 替换
在 ```/opt/atlassian/confluence/conlfluence/WEB-INF/lib``` 添加：
- ```atlassian-extras-decoder-*.jar```
- ```mysql-connector-java-*-bin.jar```

# 配置
## General Configuration
### General Configuration

#### BASE URL
若修改path，如 ```http://192.168.0.1:8080/confluence``` , 需要同时修改 ```${jira_home}/conf/server.xml``` 中 ```<Context/>``` 中 ```path="/confluence"```

#### Collaborative Editing
Restart Synchrony

### Security Configuration
- Secure administrator sessions

### 如果遇到宏中汉字显示方框
/usr/share/fonts/中添加中文字体

http://confluence/rest/cas/1.0/avatar/server/
