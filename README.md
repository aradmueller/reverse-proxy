# reverse-proxy
```
sudo mkdir -p /usr/local/lib/docker/cli-plugins
sudo curl -SL https://github.com/docker/compose/releases/download/v2.2.3/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose
sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
```



docker:
```
docker run -d --name reverse-proxy \
-v /opt/webserver/reverse-proxy/config/conf.d/:/etc/apache2/conf.d/:rw \
-v /opt/webserver/reverse-proxy/config/ssl/:/etc/apache2/ssl/:ro \
-v /opt/webserver/reverse-proxy/logs/:/var/log/apache/:rw \
-p 80:80/tcp \
-p 443:443/tcp \
 acsdatasystems/sechttpd:latest

 docker run -d --name websvc-node1 \
-v /opt/webserver/websvc-node1/config/conf.d/:/etc/apache2/conf.d/:rw
-v /opt/webserver/websvc-node1/data:/opt/websvc-data/:ro
-v /opt/webserver/websvc-node1/logs/:/var/log/apache/:rw
-p 8088:80/tcp \
 acsdatasystems/sechttpd:latest
 ```