#Companion object, Nested 클래스, Inner 클래스 비교
- companion object
  - 유효한 성질 -> 자신의 속한 outer class 의 생성자에 접근이 가능하다.심지어 private 여도 접근이 가능하다.
  - outer class 의 생성자에는 접근이 가능하지만 다른 멤버 합수, 변수 에는 접근할 수 없다.
  - outer class 의 생성 없이 사용가능
  - 자바의 static 이랑은 다르다.
- Nested class - class 안에 class
  - companion object 과 유사하게 outer class 의 생성없이 사용 가능하다.
    - Nested class 의 객체 생성은 필요하다.
    - Nested class 에서는 companion object 에 접근 가능하다.
    - 자신을 감싼 outer class 로의 접근 불가능 (outer 의 생성자는 호출 가능`)
    - outer class 에서는 Nested class 접근은 가능하다 Nested().function()...
    - Outer.Nested().greeting()
      - Outer class 의 객체 생성시 접근 가능하다고 생각하면 안된다. 거의 남남에 가깝다.
      - Outer 안에있는ㄷ Nested class 의 객체를 생성한것이다.
      - 결국 위 코드는 Outer class 안에 Nested class 를 생성하고 Nested class 안에 greeting 함수를 호출하였다.
- Inner class
  - outer class 를 생성후, inner class 생성 휴 사용.
  - Inner 라는 키워드를 사용해 클래스를 정의한다.
  - Nested class 와 달리, Outer class 에 접근가능
  - outer class 의 멤머변수에 접근가능 private 여도 가능.

- https://www.youtube.com/watch?v=nEOuwA_qx0U
- Inner
  - 너가 존재해야 내가 존재한다.
- Nested
  - 남남에 가까운 컨셉
- Companion object
  - 난 너가 존재하지 않더라도, 너만을 바라본다.




#static, object, companion object

- object declaration
  - 싱글톤 형태
  - 쓰레드 세이프함
  - 지연 초기화 (실제로 사용될 때 초기화)
  - const val 로 선언된 상수는 static 변수.
  - object 내부에 선언된 변수와 함수들은 java 의 static 이 아님.
    - 단 아래 케이스들은 static
    - const val 로 상수 선언한 것들,
    - @JVMStatic, @JVMField 애노테이션 붙은 변수 및 함수들

- companion object
  - 클래스 내부에 들어가는 블럭
    - 클래스 자체가 static 이 아님.
  - 해당 클래스가 로드될 때 초기화 됨.
  - const val 로 선언된 상수는 static 변수
  - 내부에 선언된 변수와 함수들은 java 의 static 이 아님.
    - 단 아래 케이스들은 static
    - const val 로 상수 선언한 것들,
    - @JVMStatic, @JVMField 애노테이션 붙은 변수 및 함수들

- object vs companion object 차이점  
  - 초기화 시점이 다름
  - object declaration 초기화 시점:
    - 실제로 사용될 때 initialized 된다.실제로 내부 함수에 접근해야 init 블럭이 호출
  - companion object 초기화 시점:
    - 해당 클래스가 로드될 때 initialized 된다.실제로 해당 클래스를 생성하면 companion object 내부 init 블럭 호출.

    