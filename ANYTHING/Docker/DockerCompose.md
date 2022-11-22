#Docker Compose

---
- Docker Compose 란
  - Docker Compose 는 여러 컨테이너를 모아서 관리하기 위한 툴
  - 웹서비스는 프론트엔드 서버, 데이터베이스 서버, 백엔드 서버로 이루어져 있는 경우가 많은데,
    - 각각을 docker 컨테이너로 작성하고, 연결하여 동작하기 때문에 Docker Compose 와 같은 컨테이너 관리 툴이 필요함.
  - 나아가 서비스 규모가 커지면, 복수의 컨테이너를 유지하고 관리해야 하며, 이를 위해 쿠버네티스 등의 관리 툴이 사용됨.

---
- Docker Compose yml 기본양식
  - version: "3"
    - Docker Compose 파일 포맷 버전 지정
  - services:
    - 컨테이너 설정
  - volumes:
    - 컨테이너에서 사용하는 volume 설정으로 대체 가능 (옵션)
    - docker -v 옵션과 동일한 역할
    - 여러 volume 을 지정할 수 있기 때문에, 리스트 처럼 작성
    - 특정 호스트 PC 와 연결하지 않고, 해당 볼륨을 컨테이너 삭제시에도 유지만 하고 싶을경우, 다음과 같이 설정을 해줘야함
      - 이름1:컨테이너내부경로1
      - 이름2:컨테이너 내부경로2
      - volumes:
        - 이름1:
        - 이름2:
    - docker volume ls
    - docker volume inspect {volume name}
    - docker volume rm 볼륨이름 - 볼륨 삭제
    - docker volume prune - 쓰지 않는 볼륨 삭제
  - networks:
    - 컨테이너간 네트워크 분리를 위한 추가 설정 부분 (옵션)

- 기타옵션들
  - restart
    - 컨테이너가 다운되었을 경우, 항상 재시작하라는 설정
    - restart: always
  - environment
    - Dockerfile 의 ENV 옵션과 동일한 역할
  - ports
    - Docker run 의 -p 옵션과 동일한 역할
    - yaml 문법에서 aa:bb 와 같이 작성하면 시간으로 해석하기 때문에 쌍따옴표를 붙어줘야 한다.
  - 

- docker-compose 명령어 
  - docker-compose up 실행
  - docker-compose stop 중지
  - docker-compose down 삭제

---

- docker service 띄우자.
  - wordpress
    - docker compose up
    - wordpress 로 exec -it 로 접속후, blog 파일 생성 mv * blog/ 후 exit
    - 최초 접속 -> 내주소/blog/wp-admin/install.php 해줘야함


- crontab -e
- crontab -l




