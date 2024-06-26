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
chmod +rwx 
```

### giving write permissions to a folder
```
sudo chmod a+rwx 
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

### login to mysql
```
mysql -u root -p
```

### copy config in sites-available to sites-enabled
```
sudo ln -s /etc/nginx/sites-available/fundosms.co.zw /etc/nginx/sites-enabled
```

### start mysql
```
sudo service mysql start
```

### import sql file in mysql
```
mysql -u root -p jikatino < jikatino.sql
```


### export sql file in mysql
```
mysqldump -u root -p jikatino < dump_12-01-2022.sql
```


### Increase timeout limit mysql
login to mysql and do:
```
SHOW VARIABLES LIKE "%timeout";
```
```
SET GLOBAL connect_timeout = 600; 
```

### reloading apache2
```
sudo systemctl reload apache2
```

### tail logs showing number of lines
```
tail -n 100 /var/log/fundobot.out.log
```

### copy file from server to local

#### with pem file
```
sudo scp -i test.pem root@192.123.456.789:/home/nigelreign/myscript.py /home
```

#### without pem file
```
sudo scp -i root@192.123.456.789:/home/nigelreign/myscript.py /home
```

# Install ssl certificate using certbot

```
sudo apt update
sudo apt install certbot python3-certbot-nginx
```
```
sudo certbot --nginx -d your_domain.com -d www.your_domain.com
sudo nginx -t
```
