# JPA, Hibernate, 그리고 Spring Data JPA의 차이점

* JPA 
  * Java Persistence API 의 약자로
  * 자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스
* Hibernate
  * JPA 라는 명세의 구현체
  * 인터페이스를 직접 구현한 라이브러리이다.
  * JPA 와 Hibernate 는 마치 자바의 interface 와 해당 interface 를 구현한 class 와 같은 관계.
* Spring Data JPA 
  * JPA 를 쓰기 편하게 만들어놓은 모듈
  * Repository 가 바로 Spring Data JPA 의 핵심
    * 스프링에서 제공하는 모듈 중 하나로 개발자가 JPA 를 더 쉽고 편하게 사용할 수 있도록 도와준다
    * JPA 를 한 단계 추상화시킨 Repository 인터페이스의 기본 구현체인 SimpleRepository 의 코드를 보면 내부적으로 EntityManager 를 사용하는 것을 볼 수 있다.
    * 