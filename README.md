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
