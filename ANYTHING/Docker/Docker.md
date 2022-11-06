#Docker

docker version

pull - > 이미지 다운로드

docker images

docker rmi  : 삭제

https://www.youtube.com/watch?v=SJFO2w5Q2HI&list=PLuHgQVnccGMDeMJsGq2O-55Ymtx0IdKWf&index=5

docker run -p


docker exec ws3 pwd : 컨테이너 명령어 내리기

 

docker exec -it ws3 /bin/bash : 컨테이너에 지속적인 명령어를 내리고 싶을 때 (계속 붙는다.)
-> bash shell 이 없는 경우 docker exec -it ws3 /bin/sh

run -p 8888:80 -v /TIL/ANYTHING/Docker/htdocs:/usr/local/apache2/htdocs/ httpd
->경로 설정을 잘못했는가..

---
- docker 안내서
- 설치는 그냥 docker desktop 으로 설치
  - docker version 
    - docker version 확인
  - 주요 옵션
    - ![img.png](img.png)
  - 우분투 설치 : docker run ubuntu:20.04
    - 아무런 옵션을 주지않아 바로 종료됨
  - 우분투 삭제 : docker rmi ubuntu:20.04
  - 우분투 쉘 실행: docker run --rm -it ubuntu:20.04 /bin/sh
  - CentOS 실행하기: docker run --rm -it centos:8 /bin/sh
  - 웹 어플리케이션 실행하기
    docker run --rm -p 5678:5678 hashicorp/http-echo -text="hello world"
  - # m1
  - docker run --rm -p 5678:8080 ghcr.io/subicura/http-echo --text="hello world"
    - http localhost:5678
```text
HTTP/1.1 200 OK
Content-Length: 11
Content-Type: text/plain; charset=utf-8
Date: Sun, 06 Nov 2022 00:47:41 GMT

hello world


```

- 레디스 시작
  - docker run --rm -p 1234:6379 redis
  - telnet localhost 1234
    - telnet 설치 : 
      - brew tap theeternalsw0rd/telnet
        brew install telnet
  - set hello world
    +OK
    get hello
    $5
    world quit
  - 