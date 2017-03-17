- 配置文件 nginx.conf
    - 防止 xsrf check failed
        ```
        server {
            listen 80;
            server_name localhost;
        
            location /$path/ {
                proxy_pass http://$host:$port;
                proxy_redirect off;
                proxy_set_header Referer $http_referer;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            }
        }
        ```