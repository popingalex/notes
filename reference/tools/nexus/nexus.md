```
# 修改端口与context path
# NEXUS_HOME/etc/nexus-default.properties
application-port=8081
nexus-context-path=/*/
```
# Configuration
- PyPI
    - User

    	```
        $HOME/.config/pip/pip.conf
        %APPDATA%\pip\pip.ini
        # or
        $HOME/.pip/pip.conf
        %HOME%\pip\pip.ini
    	```
    - Global

        ```
        /etc/pip.conf
        C:\ProgramData\pip\pip.ini
        ```

    ```
    [global]
    index = http://nexus_url/repo_name/pypi
    index_url = http://nexus_url/repo_name/simple
    [install]
    trusted-host = address
    ```
- npm

    ```
    # 配置仓库地址
    npm config set registry http://nexus_url/repo_name
    # 发布
    npm publish --registry http://nexus_url/repo_name
    ```
    发布模块需要将npm Bearer Token Realm添加到nexus的Active realms中
    
