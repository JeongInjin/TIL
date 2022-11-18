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
    - 
  - ENTRYPOINT
    - 
  - EXPOSE
    - 
  - ENV
    - 
  - WORKDIR
    - 
  - COPY
    - 








