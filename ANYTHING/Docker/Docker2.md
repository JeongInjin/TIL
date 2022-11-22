#DOCKER

---
- linux
- sudo apt-get update 
  - 패키지 업데이트
- ps aux | grep 프로세스
  - 프로세스가 실행 중인지 확인하고, 관련 프로세스에 대한 정보 출력
- kill -9 프로세스 ID(pid)
  - 강제 종료
- &
  - 백그라운드로 실행시킬때
- cp
  - cp A B A 파일을 B로 복사
- cp -rf * 폴더
  - 하위폴더 포함 복사하기

- 하드링크 복사
  - 레퍼런스를 공유하듯 A -> B 파일일시 B 파일을 변경해도 A파일이 변경된다.
- 소프트(심볼릭)링크
  - 바로가기 느낌
  - ln -s A B
    - ls -al 하면 소프트 링크 확인 가능

- 그외
  - sudo apt-get install vim 
    - vim 설치
  - whoami
    - 사용자 그룹보기
  - 
---
- ubuntu 20.04 에서 docker 설치
  - 최신 패키지 리스트 업데이트
    - sudo apt update
  - docker 다운로드를 위해 필요한 https 관련 패키지 설치
    - sudo apt install apt-transport-https ca-certificates curl software-properties-common
  - docker repository 접근을 위한 GPG key 설정
    - curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  - docker repository 등록
    - sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
  - 등록한 docker repository 까지 포함하여 최신 패키지 리스트 업데이트
    - sudo apt update
  - docker 설치
    - sudo apt install docker-ce
  - docker 실행 중임을 확인
    - # **`sudo systemctl status docker`**
  - docker 가 사용하고 있는 저장매체 현황 확인
    - # **`docker system df`**
    - 그외 -> 전체 저장매체 현황 확인 명령어 `df` 명령어도 있음
  - 실행중인 컨테이너 사용 리소스 확인하기
    - # **`docker container stats`**
- sudo 명령 없이 docker 명령어 사용하기
  - sudo usermod -aG docker ${USER} 
  - 터미널 끊고 다시 ssh 접속
  - 현재 ID 가 docker group 에 포함되어 있는지 확인
    - id -nG
  - sudo 없이 명령을 할 수 있음
    - docker

- ubuntu 20.04 에서 docker-compose 설치
  - release page 에서 최신 버전 확인후, 다음 링크에서 버전(1.28.2)변경
    - https://github.com/docker/compose/releases
      - 2.12.2 가 현재최신(22.11.15) 임 최신부분만 변경해 주자
      - 하지만 실습을 위해 1.28.5로..진행
        - sudo curl -L "https://github.com/docker/compose/releases/download/1.28.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  - 실행권한주기
    - sudo chmod +x /usr/local/bin/docker-compose
  - 다음 명령어 실행시 버전 확인이 가능하면 성공임
    - docker-compose --version 또는 docker-compose -v
      - docker-compose version 1.28.5, build c4eb3a1f



- docker hub 가입후 서버에서 로그인
  - `sudo systemctl status docker`
    - 항상 docker 가 running 상태여야 함.
  - docker login
    - Login Succeeded 뜨면 성공
  - docker logout
    - 로그아웃
  - 다운로드 받을 이미지 검색
    - docker search ubuntu
  - 툭정 태그 리스트 확인
    - https://hub.docker.com/_/ubuntu?tab=tags&page=1&ordering=last_updated
  - 이미지 다운
    - docker pull ubuntu
    - docker pull ubuntu:20.04
  - 이미지 확인
    - docker images, docker image ls
      - 도커 이미지 검색
    -docker images -q,  docker image ls -q
      - 도커 이미지 아이디만 표시
    - docker rmi {IMAGE ID} 또는 docker rmi ubuntu:20.04
  - docker create ubuntu
    - 컨테이너 생성
  - docker ps, docker ps -a
  - docker rm {CONTAINER ID}
    - 컨테이너 삭재
  - docker create --name {내가원하는컨테이너이름} {이미지이름}
    - ex) docker create --name myUbuntu ubuntu
      - 내가 원하는 이름으로 지정
  - docker start {CONTAINER ID}
  - docker run 
  - docker run {IMAGE} - 시작
  - docker run -it ubuntu
    - 컨테이너 실행 후 해당 ubuntu 내로 들어가서 터미널로 명령을 진행할 수 있다.
    - 컨테이너 종료시, 컨테이너도 중지됨
  - docker run -it --name myubuntu ubuntu
    - 컨테이너 이름을 원하는 이름으로 변경시
    - 컨테이너 종료시, 컨테이너도 중지됨
  - docker run -it --rm --name myubuntu ubuntu
    - 컨테이너 종료시, 컨테이너도 중지됨,
    - docker ps -a 에 해당 컨테이너가 남아있지 않음
  - docker run -it -d --name myubuntu3 ubuntu
    - 백그라운드로 시작
  - docker attach myubuntu3
    - it 모드로 접근하고싶을시
  - docker stop {CONTAINER ID}
    - docker 종료

---
- apache 웹서버 공식 docker 찾기
  - docker search httpd 또는 docker search httpd --limit=5
  - 컨테이너 pull -> container create -> docker start 식으로 가야하지만 `run`을 사용하면 합쳐서 구동됨
  - docker run httpd
  - docker run -d --name apacheweb httpd
  - docker run -d -p 9999:80 --name apacheweb httpd
    - port 연결하여 백그라운드로 실행
  - sftp 를 이용해 /home/ubuntu 에 index.html 이 든 파일 전체를 업로드
  - docker run -d -p 80:80 -v /home/ubuntu/2021_DEV_HTML:/usr/local/apache2/htdocs --name my_apache httpd
  - docker run -d -p 80:80 -v /home/ubuntu/2021_DEV_HTML:/usr/local/apache2/htdocs --name my_apache httpd:alpine
    - alpine 
      - 초경량 유틸리티만 모아논 패키지


---
- httd(apache2) it works 는 httpd 이미지의 apache 웹서버 기본 설정에 의해 /usr/local/apache2/htdocs 폴더에 있는 index.html임
- docker exec -it my_apache /bin/sh 접속
- cd /usr/local/apache2/htdocs 이동

- -d, -it 합쳐서 -dit 로도 쓰임
  - docker run -dit --name myubuntu ubuntu
    - -d 와 -it 옵션을 같이써서 bash 쪽에 못붙은상태
  - docker attach myubuntu
    - 입력창으로 붙음
  - 모든 컨테이너 중지
    - docker stop $(docker ps -a -q)
  - 모든 컨테이너 삭제
    - docker rm $(docker ps -a -q)
  - 모든 이미지 삭제
    - docker rmi -f $(docker images -q)
      - -f 옵션은 이미지 삭제가 안될경우도 있어서 넣음.
```text
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
docker rmi -f $(docker images -q)

#쓰지않는 이미지, 볼륨, 네트워크 삭제
docker system prune -a --volumes
```







