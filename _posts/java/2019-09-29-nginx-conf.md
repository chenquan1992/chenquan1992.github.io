---
layout: post_two
title: nginx 配置使用 https、wss
categories: 常用命令
description: 常用命令
keywords: 常用命令
---

***我爱你，为了你的幸福，我愿意放弃一切--包括你。***

在 Tomcat 中配置使用 https 之后，本以为可以直接使用 wss，但是尝试过好像两者不能并存，故使用 nginx 反向代理使用 wss，下面是 nginx.conf 的配置文件
```properties

worker_processes  1;

events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    sendfile        on;
    keepalive_timeout  65;

    upstream app{
        server 127.0.0.1:8081;
    }

    # 80 端口重定向到 443
    server {
        listen       80;
        # 这个服务的名字，没什么作用    
        server_name  tes.ejiot.cn; 
        return 301 https://$server_name$request_uri;
    }

    # HTTPS server
    server {
       listen       443 ssl;
       server_name  tes.ejiot.cn;

       ssl_certificate      D:/soft/nginx-1.16.0/certfile/tes.ejiot.cn.pem;
       ssl_certificate_key  D:/soft/nginx-1.16.0/certfile/tes.ejiot.cn.key;

       ssl_session_cache    shared:SSL:1m;
       ssl_session_timeout  5m;

       ssl_ciphers  HIGH:!aNULL:!MD5;
       ssl_prefer_server_ciphers  on;

       location / {
           proxy_pass   http://app/;
       }

       location /ws {
            proxy_pass http://127.0.0.1:6004/;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection "upgrade";
       }
    }

}

```



