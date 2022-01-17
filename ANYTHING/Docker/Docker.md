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