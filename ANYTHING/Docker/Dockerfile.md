#Dockerfile

---

- Dockerfile ?
  - docker 이미지를 작성할 수 있는 기능
  - Dockerfile 문법으로 이미지 생성을 위한 스크립트를 작성할 수 있고, 이를 기반으로 이미지를 생성할 수 있음
  - 나만의 이미지를 생성할 수 있고, 배포를 위해서도 많이 활용한다.

- Dockerfile 기본문법
  - 기본적으로는 간단히 명령와 인자로 이루어짐
  - 명령은 통상적으로 대문자로 작성함(소문자로 작성해도 문제없지만, 구분을 위한..)

- Dockerfile 주요 명령
  - FROM
    - 베이스 이미지 지정 명령
    - 반드시 Dockerfile 에 작성해야 하는 명령
      - docker build --tag myimage .
  - LABEL
    - 단순히 정의하는 부분, 누가적었는지, 어떤기능인지 등 (메모용도)
    - 주석과의 차이점은 이미지를 조사할경우  json 형태로 Labels 형태의 데이터가 나온다.
      - 이미지 조사하는 명령어: docker inspect myweb
  - CMD
    - docker 가 실행됐을시 실행되는 명령 || 프로그램이 있다.이를 설정하는 부분이 CMD 이다.
    - 3가지 형태로 CMD 명령을 작성할 수 있음
    - CMD 는 하나의 Dockerfile 에서 한가지만 설정되며, 만약 여러개일 경우, 맨 마지막에 설정된 CMD 설정만 적용됨.
  - RUN
    - 이미지 생성시, 일종의 layer 를 만들 수 있는 명령어로, 보통 베이스 이미지에 패키지를 설치하여 새로운 이미지를 만들 때 많이 사용 한다.
    - 
  - ENTRYPOINT
    - 명령어를 이미지에 박아 놓는다라 생각하자.
    - docker run 시에 함께 넣어지는 CMD 명령에 덮어씌워지지 않고, 반드시 실행해야 하는 명령을 기입할 때 사용
    - CMD 를 읽어들이면 ENTRYPOINT 의 인자의 역할을 한다.
  - EXPOSE
    - docker 컨테이너의 특정 포트를 외부에 오픈하는 설정
    - docker run -p 옵션으로 설정할 수도 있음
      - 해당 옵션은 컨테이너의 특정 포트를 외부에 오픈하고, 해당 포트를 호스트 pc 의 특정 포트와 매핑시킴
    - EXPOSE 는 컨테이너 생성시, 특정 포트를 외부에 오픈하는 것만 설정하는 것임
      - 따라서 독립적으로 실행시는 EXPOSE 옵션을 넣는다고 해서, 호스트 PC 에서 해당 컨테이너에 포트번호로 접속할 수 있는 것은 아님
    - EXPOSE 80 으로 설정 후, -P(대문자) 옵션을 쓰면, EXPOSE 로 오픈된 포트에 호스트 PC 의 랜덤 포트가 매핑됨 
      - docker run -P -d myweb
          - docker ps 로 확인하면 0.0.0.0:49153->80/tcp 랜덤으로 부여됨
    - 
  - ENV
    - 컨테이너 내의 환경변수 설정
    - 설정한 환경변수는 RUN, CMD, ENTRYPOINT 명령에도 적용됨.
  - WORKDIR
    - RUN, CMD, ENTRYPOINT 명령이 실행될 디렉토리 설정
  - COPY
    - 파일 또는 디렉토리를 docker 컨테이너에 복사. ADD 와 달리 URL 은 지정할 수 없으며, 압축 파일을 자동으로 풀어주지 않음.


---
- 가끔사용
- Docker logs {컨테이너 id 또는 name}
  - docker container 표준 log
- Docker kill {컨테이너 id 또는 name}
  - stop 은 즉시 컨테이너 중단하지 않지만, kill 은 즉시 중지함.

- CMD 부분을 ["bin/sh"] 만 있더라도 옵션을 주어 CMD 를 덮을 수 있다.
  - docker run -dit -p 9999:80 --name httpdweb2 myweb2 /bin/sh -c httpd oreground
  - docker inspect {컨테이너 id 또는 image name}
- 


