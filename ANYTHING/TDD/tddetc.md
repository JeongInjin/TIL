#tdd etc

- tdd 테크닉
  - Assert First
    - assert 부터 거꾸로 작성하는 것(then 부분부터 작성)
    - 컴파일 에러, 익셉션 에러 등 이 계속 날것인데 이런것들을 정리하면서
  - 단순한부터 복잡함까지
    - 정말 단순한것부터 작성하여 복잡한것 까지 순차적으로 진행
  - 기타 코드는 library-app(kotlin) 을 참고하자 test_technique

---
- Right-BICEP (무엇을 테스트할지)
  - Right: 결과가 올바른가?
  - B: 경계조건(boundary conditions)은 맞는가?
  - I: 역 관계(inverse relationship)를 검사할 수 있는가?
  - C: 다른 수단을 활용하여 교차 검사(cross-check)할 수 있는가?
  - E: 오류 조건(error conditions)을 강제로 일어나게 할 수 있는가?
  - P: 성능 조건(performance characteristics)은 기준에 부합하는가?
  - 

