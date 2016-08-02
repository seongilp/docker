# Docker


## Docker Command Usage
```
search 	// 이미지 검색하기
pull 	// 이미지 받기
images 	// 이미지 목록 출력하기
run 	// 컨테이너 생성하기
ps 	    // 컨테이너 목록 확인하기
start 	// 컨테이너 시작하기
restart // 컨테이너 재시작하기
attach 	// 컨테이너에 접속하기
exec 	// 외부에서 컨테이너 안의 명령 실행하기
stop 	// 컨테이너 정지하기
rm 	    // 컨테이너 삭제하기
rmi 	// 이미지 삭제하기

```

## Wordpress / MariaDB / Phpmyadmin
```
docker-compose up -d
```

### docker-compose.yml
```
wordpress:
  image: wordpress
  links:
    - wordpress_db:mysql
  ports:
    - 8080:80
    volumes:
      - ~/workspace/wordpress/webroot:/var/www/html
wordpress_db: 
  image: mariadb
  environment:
    MYSQL_ROOT_PASSWORD: examplepass
  volumes:
      - ~/workspace/wordpress/dbroot:/var/lib/mysql
phpmyadmin: 
  image: corbinu/docker-phpmyadmin
  links:
    - wordpress_db:mysql
  ports:
    - 8181:80
  environment:
    MYSQL_USERNAME: root
    MYSQL_ROOT_PASSWORD: examplepass
```

## Ghost
```
docker pull ghost
docker run  -d --name ghost -p 8084:2368 -v /home/zihado/workspace/ghost:/var/lib/ghost ghost
config.js 수정 필요 
url: 'http://zihado.com'
```

## Redmine
```
docker run --name=postgresql-redmine -d \
  --env='DB_NAME=redmine_production' \
  --env='DB_USER=redmine' --env='DB_PASS=password' \
  --volume=/home/zihado/workspace/redmine/postgresql:/var/lib/postgresql \
  sameersbn/postgresql:9.4-24

  docker run --name=redmine -d \
  --link=postgresql-redmine:postgresql --publish=10083:80 \
  --env='REDMINE_PORT=10083' \
  --volume=/home/zihado/workspace/redmine/redmine:/home/redmine/data \
  sameersbn/redmine
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
- [http://pyrasis.com/docker.html](http://pyrasis.com/docker.html)
