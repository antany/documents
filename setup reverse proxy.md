# documents

```
server {
    listen 80;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    ssl_certificate      /etc/nginx/keys/certificate.pem;
    ssl_certificate_key  /etc/nginx/keys/certificate.pem.key;
    ssl_session_cache    shared:SSL:1m;
    ssl_session_timeout  5m;
    ssl_protocols        TLSV1.1 TLSV1.2 TLSV1.3;
    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers  on;
    location / {
        proxy_set_header        Host $host;
        proxy_set_header        X-Real-IP $remote_addr;
        proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header        X-Forwarded-Proto $scheme;
        proxy_pass https://localhost:8443;
        proxy_read_timeout 90;
        proxy_ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    }
}
```
