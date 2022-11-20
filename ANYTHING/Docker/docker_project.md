#docker project

---
- docker run -dit -p 80:8080 --name myos ubuntu:20.04
- docker exec -it myos /bin/bash 
  - apt-get update
  - apt-get install nginx=1.18.0-0ubuntu1.4 (1.4가 아닐 수 있음 계속 올라감)
    - apt-cache policy nginx 로 확인하여 installed 버전 확인
  - find -name nginx.conf 에 기본 설정파일을 찾을 수 있음
  - 크게 설정은
    - user
      - 웹서버를 돌리는 아이디
      - default 로 보통은 냅둔다.
    - worker_processed
      - 프로세스를 몇개 만들것인지
      - default 로 보통은 냅둔다.
    - pid
      - default 로 보통은 냅둔다.
    - events
      - default 로 보통은 냅둔다.
    - http
      - 필요시 찾아서...
      - include 부분을 잘 살펴보자..
      - /etc/nginx/sites-enabled 에 default 파일이 심볼리 링크로 /etc/nginx/sites-available/default 걸려있음
      - 실직적인 파일은 /etc/nginx/sites-available 에 있음

  - nginx default 에 있는 설정
    - server
      - liten 은 HTTP 요청을 받을 포트 설정
      - default_server 는 모든 웹서버 요청을 받는다는 의미
      - 두번째 줄 liten 은 IPv6 포트 관련 설정이므로 무시해도 됨.
    - server_name
      - 요청을 받을 도메인 이름 설정
      - localhost 나 별도 도메인이 없다면 기본 설정으로.
      - 도메인이 있다면 ex)abc-coding.org www.abc-coding.org; 식으로 입력
    - root
      - 기본 루트 
    - location 설정
      - location 기본 설정 이해
        - 웹서버 주소에 따라, 요청되는 파일을 찾을 디폴트 폴더를 root 로 설정하고
        - location 설정으로 웹서버 주소에 따른 폴더를 변경할 수 있음
        - index 는 해당 웹서버 주소 요청시, 디폴트로 응답할 index.html 파일명 설정
          - 예를 들어, PHP 언어를 쓴다면, index.php 로 디폴트 파일을 설정하기 위해 설정
    - 





