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

- 자바 <-> 코틀린 변환중
  - service 단에서 @Transactional 을 이용하려니 "kotlin Methods annotated with '@Transactional' must be overridable" 라는 문구가 나옴
    - private 는 @Transactional 이 적용되지 않는다.
    - @Transactional 는 Proxy 형태로 동작하기 때문에 외부에서 접근 가능한 서비스만 @Transactional 설정이 가능함.
    - 코틀린은 기본이 상속을 허용하지 않음 open class, open fun 식으로 해줄 수 있으나 귀찮음
    - plugins(...) 에 id 'org.jetbrains.kotlin.plugin.spring' version '1.6.21' 를 추가해 주자.
      - all-open
      - 해당 플러그인을 사용하면 아래 어노테이션이 있으면 all-open 을 자동으로 추가시켜줌
        - @Component
          @Async
          @Transactional
          @Cacheable
          @SpringBootTest
          @Configuration, @Controller, @RestController, @Service, @Repository, @Component

- 자바 <-> 코틀린 변환중
  - Resolved [org.springframework.http.converter.HttpMessageNotReadableException: JSON parse error: Cannot construct instance of `com.group.libraryapp.dto.book.request.BookRequest`
  - Json 파싱 에러
  - build.gradle > dependencies{...} 부분에 implementation 'com.fasterxml.jackson.module:jackson-module-kotlin:2.13.3' 추가해주자

