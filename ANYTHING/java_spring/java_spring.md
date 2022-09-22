#filter, interceptor, aop


- 서블릿 필터
  - 서블릿 에서 제공, Dispatcher Servlet 에 요청이 전달되기 전, 후에 부가작업을 처리하는 객체
  - init - default method
    - 톰캣(서블릿과 웹서버 역할을 제공하는 java 기반 웹 서버환경)이 시작이되고 커넥션 풀도 연결되고 init 이 호출됨
    - 1번만 호출됨.
  - doFilter - 필수 오버라이딩 필요
    - 필터 체인형식으로 가능.
    - chain.doFilter 를 반드시 호출해야지 다음으로 넘어감.
  - destroy - default method
    - 소멸이 될때 1번만 호출이 된다.


- 인터셉터
  - 스프링이 제공하는 기술로, 디스패처 서블릿이 컨트롤러를 호출하기 전, 후 요청에 부가적인 작업을 하는 객체.
  - preHandle
  - postHandle
  - afterCompletion


- 필터 인터셉터 차이
    -
- 필터 - 자바 표준 스펙, 필터에서 예외가 발생하면 @ControllerAdvice 에서 처리하지 못함
- 인터셉터 - 스프링이 제공하는 기술, 예외가 발생하면 @ControllerAdvice 처리 가능,afterCompletion 가능
  - @ControllerAdvice 의 적용범위 : Dispatcher Servlet 이기때뮨에.
  