## Repository
### 配置
- MEM 4GB | CPU 2Core | DISK 1TB
- 172.17.38.63

### 服务
- 8081/nexus | Nexus Develop

## SCM
### 配置
- MEM 4GB | CPU 2Core | DISK 1TB
- 172.17.38.56

### 服务
- gitlab | Gitlab

## CI-Master
### 配置
- MEM 4GB | CPU 2Core | DISK 500GB
- 172.17.38.85

### 服务
- 8080/jenkins | Jenkins Master
- SonarQube Server
- 10389        | ApacheDS
- 3306         | MySQL
  - sonardb

## CI-Client
### 配置
- MEM 4GB | CPU 2Core | DISK 500GB
- 172.17.38.59

### 服务
- Jenkins Slave
- Sonar Scanner

## Atlassian
### 配置
- MEM 4G | CPU 2Core | DISK 100GB
- 172.17.38.86

### 服务
- 8080/jira       | Atlassian JIRA
- 8090/confluence | Atlassian Confluence
- 3306            | MySQL
    - jiradb
    - confluencedb

## Monitor
### 配置
### 服务
- Zabbix
- ELK
