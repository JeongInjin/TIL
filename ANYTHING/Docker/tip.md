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
    - sudo systemctl status docker

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



