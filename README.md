# test1
docker with certbot and letsencrypt
\
\
to delete all images:
```
docker rmi -f $(docker images -aq)
```
\
to navigate inside a running docker container:
```
docker exec -it <container> bash
...
exit
```
\
just renewing a certificate is not enough  
the docker container needs be restarted as well:
```
docker-compose restart
```