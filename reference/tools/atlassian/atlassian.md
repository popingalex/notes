- 国内下载
    - [JIRA](http://www.fangwai.net/software/jira/download/)
    - [Confluence](http://www.fangwai.net/software/confluence/download/)
    - [Atlassian](http://www.confluence.cn/pages/viewpage.action?pageId=6722516)

    > JDK1.8(避免使用JDK ```1.8._25```，```1.8._31```)

- DB
    jira 与 confluence 均需要数据库支持

- [with MySQL5.7](https://github.com/yurii-github/mysql-connector-j)
    > This fork provides hardfix. It was made to replace deprecated "storage_engine" variable to "default_storage_engine", so apps can work with MySQL 5.7 instead of throwing exception.
- mysql-connector复制到/lib下
- 汉化文件复制到/atlassian-jira/WEB-INF/lib下
- 破解文件复制到/atlassian-jira/WEB-INF/lib并替换
- admin/admin123


```
BCVQ-X1ST-JY0W-B1PP
```

- 配置
    - [LDAP](https://confluence.atlassian.com/adminjiraserver071/connecting-to-an-ldap-directory-802592350.html)
    - [FuckCrowd](https://jira.atlassian.com/browse/CONF-21980)
