# Docker

## Dokcer Installation
```
sds
```

## Docker Command Usage
```
docker ps -a
docker pull XXX
docker image
docker rm
```

## Guacmole
```
docker pull mattgruter/guacamole-guacd
docker pull mattgruter/guacamole-db
docker pull mattgruter/guacamole-webserver
```

```
docker run -d --name guacd mattgruter/guacamole-guacd
docker run -d --name db mattgruter/guacamole-db
docker run -d --link guacd:guacd --link db:db -p 8080:8080 mattgruter/guacamole-webserver
```

## Useful Links
- 
