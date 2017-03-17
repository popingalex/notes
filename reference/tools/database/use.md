> 配置%可以从任意地址访问，localhost则只能本地访问

- JIRA
```MySQL
CREATE DATABASE jiradb CHARACTER SET utf8 COLLATE utf8_bin;
GRANT all on jiradb.* to 'jira'@'%' identified by 'jira123';
flush privileges;
```

- CONFLUENCE
```MySQL
CREATE DATABASE confluencedb CHARACTER SET utf8 COLLATE utf8_bin;
GRANT ALL ON confluencedb.* to confluence@'%' identified by 'confluence123';
flush privileges;
```


- Fisheye
```MySQL
CREATE DATABASE fisheyedb CHARACTER SET utf8 COLLATE utf8_bin;
GRANT ALL ON fisheyedb.* to fisheye@'%' identified by 'fisheye123';
flush privileges;
```

- SONAR
```MySQL
CREATE DATABASE sonardb CHARACTER SET utf8 COLLATE utf8_bin;
GRANT ALL ON sonardb.* to sonar@'%' identified by 'sonar123';
flush privileges;
```
