# 地址配置 ```external_url```

https://docs.gitlab.com/omnibus/settings/configuration.html#configuring-the-external-url-for-gitlab

# 账号配置 ```gitlab_rails['ldap_enabled'] = true```
# 邮件配置 ```gitlab_rails['smtp_enabled'] = true```

# 配置文件 ```/etc/gitlab/gitlab.rb```

# 应用配置 ```gitlab-ctl reconfigure```
# 重启服务 ```gitlab-ctl restart```

# 备份恢复
## 备份命令 ```gitlab-rake gitlab:backup:create```
## 备份目标 ```gitlab.rb``` 中 ```gitlab_rails['backup_path']```
https://docs.gitlab.com/ce/raketasks/backup_restore.html#create-a-backup-of-the-gitlab-system

```*_DATE_gitlab_backup.tar /var/opt/gitlab/backups/```

```gitlab-rake gitlab:backup:restore BACKUP=*_DATE```
http://docs.gitlab.com/ce/install/relative_url.html#relative-url-requirements

```gitlab-rake cache:clear RAILS_ENV=production```

gitlab_rails['gravatar_plain_url']
