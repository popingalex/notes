- [centos7](http://www.server-world.info/en/note?os=CentOS_7&p=openldap)
- 模块
    ```
    openldap
    openldap-devel
    openldap-clients
    openldap-servers
    ```
- [配置文件](http://wangzan18.blog.51cto.com/8021085/1835595)
    ```
    /usr/share/openldap-servers/slapd.conf
    # 或者
    /usr/local/etc/openldap/slapd.conf.default    
    #拷贝至
    /etc/openldap/slapd.conf

    /usr/share/openldap-servers/DB_CONFIG.example
    #拷贝至
    /var/lib/ldap/DB_CONFIG

    #移除slapd.d/*
    rm -rf /etc/openldap/slapd.d/*
    #重建
    slaptest -f /etc/openldap/slapd.conf -F /etc/openldap/slapd.d
    #权限
    chown -R ldap:ldap /etc/openldap/slapd.d

    ldapsearch -x -D "cn=***,dc=***,dc=***" -W [-b "dc=***, dc=***"] [-LLL]
    # -W 询问密码 或 -w 密码

    #初始配置文件 /etc/openldap/base.ldif
    dn: dc=***,dc=com
    objectClass: organization
    objectClass: dcObject
    dc: ***
    o: ***

    dn: ou=people,dc=***,dc=com
    objectClass: top
    objectClass: organizationalUnit
    ou: people

    dn: ou=group,dc=***,dc=com
    objectClass: top
    objectClass: organizationalUnit
    ou: group

    ldapadd -x -D "cn=***,dc=***,dc=***" -w 密码 -f 配置文件
    ```

- 设置密码
    ```
    slappasswd
    ```
- 配置
    ```
    Common Name
    Domain Component
    Distinguish Name
    Organizational Unit
    ```

    cn = gsafety
    dc = gsafety
    dc = com
- phpLDAPadmin
    - 登录使用CN : cn=***,dc=***,dc=***

cn=admin,dc=gsafety,dc=com/admin123
