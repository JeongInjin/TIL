#에러 해결

- 자바 <-> 코틀린 코드 변경중 코틀린 class 에 @Entity 를 붙이면 아래와 같이 에러 문구가 나온다면
- Class 'Book' should have [public, protected] no-arg constructor
  - 자바
    - @Entity,@Embeddable 어노테이션을 사용하면 이 클래스는 테이블과 매핑할 클래스라는 것을 명시해준다.
    - 이때 반드시 기본 생성자가 필수적임.
    - @RequiredArgsConstructor 붙여주던지, 기본 생성자를 입력해주자.
  - 코틀린
    - build.gradle 쮹에 plugins (...) ...쪽에 
    - id 'org.jetbrains.kotlin.plugin.jpa' version '1.6.21' 를 붙여준뒤, 해결이 안되면 껏다 키자.


- 자바 <-> 코틀린 변환중
- Caused by: java.lang.NoClassDefFoundError: kotlin/reflect/full/KClasses 뜬다면
- 코틀린 클래스에 대해 리플렉션을 못한다..
  - build.gradle > dependencies(...) 부분에 implementation 'org.jetbrains.kotlin:kotlin-reflect:1.6.21' 을 추가해 주자.


