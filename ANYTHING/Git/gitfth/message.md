#AngularJS Commit Message Conventions
- https://gist.github.com/stephenparish/9941e89d80e2bc58a153
- https://velog.io/@outstandingboy/Git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%8B%9C%EC%A7%80-%EA%B7%9C%EC%95%BD-%EC%A0%95%EB%A6%AC-the-AngularJS-commit-conventions



---
- commit 메세지는 영어가 좋다.....음.. 
```text
{title}
  (공백)
{contens}

title 작성 방법:
jira 나 다른 이슈트래커 를 사용하고 있다면 이슈넘버를 적어주자.
이슈넘버 뒤에 제목을 적어주는데 현재형 동사로 적어준다.
ex)MTH-611 Implement breaking new feature

blabla
```
- push 전 마지막 commit 메세지 다시 작성시
  - git commit --amend -m "ADD 블라블라블라"


- 좋은 커밋 작성법 ->
- 커밋 유형 지정
  - FEAT : 새로운 기능의 추가
  - FIX: 버그 수정
  - DOCS: 문서 수정
  - STYLE: 스타일 관련 기능(코드 포맷팅, 세미콜론 누락, 코드 자체의 변경이 없는 경우)
  - REFACTOR: 코드 리펙토링
  - TEST: 테스트 코트, 리펙토링 테스트 코드 추가
  - CHORE: 빌드 업무 수정, 패키지 매니저 수정(ex .gitignore 수정 같은 경우)



- 제목 행의 첫 글자는 대문자로 시작
- 제목 행은 너무 길지않게(50자 이내)
- 제목 뒤에는 한줄 띄워 본문과의 분리
- 제목 행 끝에 마침표는 쓰지 않기
- 제목 행에 명령문을 사용한다: 명령이나 설명하듯이 작성
- 본문은 적당히 끊어 줄을 바꿔준다(72자)
- 본문에 변경 한 내용과 이유 설명: 어떻게 보다는 무엇과 왜를 설명
- 검토자가 원래 문제가 무엇인지 이해한다고 가정하지 말고 확실하게 설명 추가
- 자신의 코드가 직관적으로 바로 파악 할 수 있다고 생각하지 말자.

