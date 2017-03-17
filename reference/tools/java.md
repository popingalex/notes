```shell
# 通常存放位置
/usr/lib/java-*.*
tar -xvzf jdk-*.tar.gz -C /usr/lib

# 环境变量
# 在/etc/profile中添加
# JAVA
JAVA_HOME=/usr/lib/java...
JRE_HOME=$JAVA_HOME/jre

CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib

PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin

export JAVA_HOME JRE_HOME CLASSPATH

export PATH
# 执行
source /etc/profile

# 配置命令
update-alternatives --install LINK NAME PATH PRIORITY
- LINK:/usr/bin/java, /usr/bin/javac
- NAME:java, javac
- PATH:$JAVA_HOME/bin/java, $JAVA_HOME/bin/javac
- PRIORITY:优先级 (例如300)
# 选择要使用的版本
update-alternatives --config NAME
```
