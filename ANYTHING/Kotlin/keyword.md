#Unit 이란 타입..

- Java 의 void 타입이 있는데...굳이..?
- 코틀린 코드를 JVM 으로 컴파일하면 Unit 은 다음과 같이 두가지 경우로 컴파일이 된다.
  - 함수의 반환 타입이 Unit 이고 함수가 제네릭 함수를 오버라이드하지 않는다면, 자바로 컴파일될 때 void 함수로 컴파일된다.
  - 위의 조건이 아니면 Unit 으로 컴파일된다.
- 코틀린은 왜 void 가 아닌 Unit 을 만들었을까?
  - 코틀린의 Unit 은 자바의 void 와 다르게 두 가지 특징이 있습니다.
  - Unit 은 싱글톤 인스턴스, 코틀린에서는 Unit 이라는 키워드는 타입이면서 동시에 객체이기도 하다.
    - `val unit: Unit = Unit`
  - Unit 은 객체이기도 하기 때문에, Any 의 자식이다. 따라서 Unit 도 Any 의 서브 클래스이다.
    - `val unit: Any = Unit`

---
#Nothing
- Nothing 은 어떠한 값도 포함하지 않는 타입
- Nothing 은 private constructor 로 정의되어 있어 인스턴스를 생성할 수 없다.
- 언제 활용될까
  - 리턴 될 일이 없을경우, 또는 예외를 던질 경우
- Nothing? 을 할 경우에는
  - null 을 return 한다는 선택지만 늘어난다
- 1.종료되지 않는 함수
- 2.예외를 던지는 함수
- 3.null 을 리턴하는 함수
- Nothing 은 모든 타입의 서브타입이다.
- 이펙티브 코틀린 item7 - 결과 부족이 발생할 경우 null 과 Failure 를 사용하라.(test 코드참고.)

---


