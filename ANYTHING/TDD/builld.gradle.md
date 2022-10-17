#설정..

- junit-vintage-engine가 exclude 되어 있는 이유
```kotlin
        testImplementation("org.springframework.boot:spring-boot-starter-test") {
            exclude(group = "org.junit.vintage", module = "junit-vintage-engine")
        }
        testImplementation("org.junit.vintage:junit-vintage-engine") {
            exclude(group = "org.junit.vintage", module = "junit-vintage-engine")
        }
```

- JUnit 5 = JUnit Platform + JUnit Jupiter + JUnit Vintage
- 위와 같이 Junit5는 3가지 하위 프로젝트의 여러 모듈로 구성되어 있다.
- JUnit Platform  JVM 기반 테스트 프레임워크를 실행시키기 위한 모듈
  - 또한 JUnit4 환경에서도 플랫폼 모듈을 진행하는 테스트를 위해 Runner를 제공한다.
- JUnit Jupiter
   - JUnit5에서 테스트 및 확장을 작성하기 위한 프로그래밍 모델 + 확장 모델이다.
- JUnit Vintage
   - JUnit3, JUnit4 기반의 테스트를 JUnit Platform에서 실행시키기 위한 TestEngin을 제공하는 모듈

- vintage 는 이름에서 보이듯이 예전 버전과의 호환을 위해 존재한다. spring-boot-starter-test는 JUnit4를 가지고 있으며, 개발자가 선택해서 테스트 코드를 작성할 수 있게 한다.


