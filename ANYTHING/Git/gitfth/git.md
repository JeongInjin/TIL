# git.bash 실습. 생활코딩 최고 ?:)

git init   - git 저장소 초기화  
ls -al - 현재 파일 목록  

- vim f1.txt  - 파일생성 (i - insert모드 , : wq 저장후 종료)  
- cat f1.txt - vim 모드가 아닌 상태로 소스보기  
- git status -
- git add f1.txt
- git config --global user.name jeong  
- git config --global user.email snowwwww12@gmail.com
- git commit - > vim으로 이동됨
- git log - 로그보기
- 소스 수정시 - > git add ... -> commit & message -> git log
- cp f1.txt f2.txt - 파일 복사


- git log -p - 커밋과 커밋사이의 소스상 차이점을 보는 명령어
- git log 0d3f71cc74d56ef1cfdb82e959d81417247b13a0 -> 해당 고유번호 이전 커밋내용만 본다.
- git diff f0350c2440c3c5bb1cf95f51c54c77614793157c..485793a571d8e6f6192fdeace14d46da4967108a 각각 고유번호 사이의 차이점을 나타내 준다.
- git diff - 어떠한 작업을 진행했는지 알 수 있다.


- reset VS revert
- git reset 0d3f71cc74d56ef1cfdb82e959d81417247b13a0 --hard => git log 에 고유번호 로 돌아간다.
- 공유를 하고나서는 절대로 reset 하지않는다.
- revert 또한 되돌리수 있지만 현재상태에서는 배우지 않는다.


- git 명령어 빈도 높은 순
- commit, push, pull, clone, checkout, add
- branch, log, diff, fetch, merge, init
- tag, rebase, rm, show, bisect, grep, mv

- git commit --help
- git commit -am "message"


- git의 원리 - with : gistory
- add, commit - objects 파일안에 내용이 저장된다. index에 파일에 파일명이 저장된다.(해시)
* add시 - 파일의 이름이 다르더라도 내용이 같다면 같은 주소값을 가진다.ex)파일 복사시, 또는 전세계적으로도.
  * objects 파일명 안에 담긴다. 
  * object 파일명의 원리(내용이 같으면 관리하는 파일 이름이 같다)
    * 아마 내용을 깃이 살펴보고 부가적인 설정을 더하여 sha1 해시값으로 변경하기 때문이다.
* commit - objects 파일에 담긴다.
  * parent가 생긴다 -> 이전 커밋을 가르킨다.
  * commit 안에 tree - 현재 해시값, parent 등 오브젝트값 등이 담겨있다.
  * object 파일안의 내용 3가지
    * 파일의 내용을 담고있는 블랍(blob)
    * 어떤 디렉토리의 파일명과 그 파일명의 내용에 대한 블랍을 담고있는 파일
    * 커밋파일
  * status - 추론 : index 파일안에 해시값을 비교하여, status 값을 나타낼 듯 하다.
  
* branch -  
* git branch
* git branch exp - > 새로운 branch만들기
* git checkout exp - > branch 변경
* 브랜치 변경후 commit 후 git log 살펴보면 브랜치 별로 로그가 다르다.
* 파일을 열고 브랜치를 변경하면 파일 구성도 새롭게 적용된다.




