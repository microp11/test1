# test1
docker with certbot and letsencrypt
\
\
to delete all images:
```
$ docker rmi -f $(docker images -aq)
```
\
to navigate inside a running docker container:
```
$ docker exec -it <container> bash
...
# exit
```
\
just renewing a certificate is not enough  
the docker container needs be restarted as well:
```
$ docker-compose restart
```
\
The certificate needs be updated every so often. Still not quite clear 100%.  
The documentation is from: https://mindsers.blog/post/https-using-nginx-certbot-docker/  
To test if everything ok, run:
```
$ docker-compose run --rm  certbot certonly --webroot --webroot-path /var/www/certbot/ --dry-run -d egcs24.com
```
The certificate last only 3 months. Set up for automatic renewal or do it manually:
```
$ docker compose run --rm certbot renew
```
followed by a container restart:
```
$ docker-compose restart
```