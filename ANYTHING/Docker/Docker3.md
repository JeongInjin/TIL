#DOCKER

---
- docker history
  - 이미지 히스토리 확인
- docker commit
  - 컨테이너 변경사항을 이미지 파일로 생성
  - 컨터이너 추가 작업을 한 뒤 컨테이너 삭제하면 사라지는데 그 작업까지 layer 로 만들어 추가로 이미지를 생성한다.
  - ex)exec -it 로 /etc/apache2/sites-available 경로에 접근, vi 모드가 없을경우
    - apt-get update
    - apt-get install vim
    - exit
    - docker commit -m "add vim" mywebserver viweb
    - docker history viweb
      - add 확인
    - docker diff : 순서는 보장하지 않음
      - A: 파일또는 디렉토리 추가
      - D: 파일또는 디렉토리 삭제
      - C: 파일또는 디렉토리 수정
    - docker inspect: 이미지와 컨테이너 세부사항 확인
    - docker logs: 컨테이너의 출력결과(STDOUT)를 확인
    - 