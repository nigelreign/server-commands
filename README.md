# Supervisor

### Installing supervisor
```
sudo apt update && sudo apt install supervisor
```

### Check supervisor status
```
sudo systemctl status supervisor
```

### Reread supervisor
```
sudo supervisorctl reread
```

### Update supervisor
```
sudo supervisorctl update
```

### starting an app

cd /etc/supervisor/conf.d

create a file test.conf

```
[program:test]
command = /bin/bash -E -c /home/test/start_app.sh
directory = /home/tes/
user = root
autostart=true
autorestart=true
stopasgroup=true
killasgroup=true
stderr_logfile=/var/log/test.err.log
stdout_logfile=/var/log/tes.out.log

```

### giving permissions to a file

```
chmod +rwx nigel.app
```

### restart nginx
```
sudo systemctl restart nginx
```

### nginx status
```
sudo systemctl status nginx
```

### pointing django app to a domain or ip and port

```
server {
    listen 80;
    server_name mydomain.co.zw;

    location = /favicon.ico { access_log off; log_not_found off; }
    location /static/ {
        root /home/test;
    }
    location / {
        include proxy_params;
        proxy_pass http://0.0.0.0:8000;
        proxy_connect_timeout 1800s;
        proxy_read_timeout 1800s;
    }
}

```
