# 스프링 시큐리티 기본 API 및 Filter 이해

---
1.프로젝트 구성 및 의존성 추가
* 인증 api 스프링 시큐리티 의존성 추가 시 일어나는 일들
  * 서버가 기동되면 스프링 시큐리티의 초기화 작업 및 보안 설정이 어루어진다.
  * 별도의 설정이나 구현을 하지않아도 기본적인 웹 보안 기능이 현재 시스템에 연동되어 작동함
    * 모든 요청은 인증이 되어야 자원에 접근이 가능하다.
    * 인증 방식은 폼 로그인 방식과 httpBasic 로그인 방식을 제공한다.
    * 기본 로그인 페이지 제공한다.
    * 기본 계정 한 개 제공한다.
---
2.사용자 정의 보안 기능 구현
* 초기화시
  * WebSecurityConfigurerAdapter - 스프링 시큐리티의 웹 보안 기능 초기화 및 설정
    * -> HttpSecurity - 세부적인 보안 기능을 설정할 수 있는 API 제공
  * SecurityConfig 를 생성하여 WebSecurityConfigurerAdapter 를 상속받아 사용자 보안 기능을 구현한다.
    * HttpSecurity 를 parameter 로 받는 configure 메서드를 Override 할 것.
      * 인증 및 인가 처리를 할 수 있다.

* 초기화 과정
  * WebSecurityConfigurerAdapter 클래스의 getHttp() 호출 httpSecurity 생성 -> applyDefaultConfiguration 호출하여 11개정도의 설정정보를 호출하며 초기화
  * configure 호출
  * anyRequest() -> 어떠한 요청에도
  * authenticated() -> 인증을 받도록 설정

* @EnableWebSecurity ?
  * WebSecurityConfiguration 설정 클래스, 여러 클래스를 임포트하여 실행시키는 클래스
  * 해당 기능을 적어줘야 시큐리티가 작동한다.

초기 설정은 application.yml -> spring.security.user.name / password 로 초기 로그인 설정 값을 줄 수 있다.

---
