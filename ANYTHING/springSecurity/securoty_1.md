#security 작업

* 스프링 시큐리티 의존성 추가
```
  implementation 'org.springframework.boot:spring-boot-starter-security'
```

* 스프링 시큐리티의 의존성 추가 시 일어나는 일들
  * 서버가 기동되면 스프링 시큐리티의 초기화 작업 및 보안 설정이 이루어진다
  * 별도의 설정이나 구현을 하지 않아도 기본적인 웹 보안 기능이 현재 시스템에 연동되어 작동함
  * 모든 요청은 인증이 되어야 자원에 접근이 가능하다
  * 인증 방식은 폼 로그인 방식과 httpBasic 로그인 방식을 제공한다
  * 기본 로그인 페이지 제공한다
/  * 기본 계정 한 개 제공한다 – username : user / password : 랜덤 문자열


* web.ignoring 설정 
```
    @Override
    public void configure(WebSecurity web) throws Exception {
        // 정적 파일들은 보안 filter 를 거치지 않고 통과된다. StaticResourceLocation 를보면 정적파일이 선언되어 있다
        // permitAll 과 기능은 비슷하지만 다른점은 permitAll 은 필터를 거쳐 통과된지만 해당 설정은 보안필터 자체를 거치지 않는다.
        // 보안 필터를 거치지않아 비용적인 면에서 낫다.
        web.ignoring().requestMatchers(PathRequest.toStaticResources().atCommonLocations());
    }
```

---
* DB 연동 인증처리 1
  * CustomDetailsService 생성후 UserDetailsService 인터페이스를 상속받아 loadUserByUsername 를 override 함
  * security.core.userdetails 의 User 를 상속받은 AccountContext 를 생성하였음.
    * UserDetails 를 반화하는 구현부
  * SecurityConfig 에 configure override 메서드 생성(login 시도 시 해당 로직을 태우기 위함)

    

