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

- 


