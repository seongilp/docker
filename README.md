# Docker


## Docker Command Usage
```
search 명령으로 이미지 검색하기
pull 명령으로 이미지 받기
images 명령으로 이미지 목록 출력하기
run 명령으로 컨테이너 생성하기
ps 명령으로 컨테이너 목록 확인하기
start 명령으로 컨테이너 시작하기
restart 명령으로 컨테이너 재시작하기
attach 명령으로 컨테이너에 접속하기
exec 명령으로 외부에서 컨테이너 안의 명령 실행하기
stop 명령으로 컨테이너 정지하기
rm 명령으로 컨테이너 삭제하기
rmi 명령으로 이미지 삭제하기
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
