#Grammar

- 싱글톤 사용하기
  - 자바와 다르게 object 이라는 키워드를 사용하면 싱글톤 패턴이 구현된다..
```kotlin
object SingletonClass {
}


//인스턴스 비교
object SingletonClass {
  val sampleString = "Sample String"
}

fun main() {
  if (SingletonObject.sampleString == SingletonObject.sampleString)
    println("동등성 비교 true")

  if (SingletonObject.sampleString === SingletonObject.sampleString)
    println("동일성 비교 ture")
}

//동등성 비교 true
//동일성 비교 true
```
- 단점
  - object 자체가 프로세스 실행시 메모리에 바로 올라가는 것은 막지 못하지만, 내부 변수들을 by lazy 를 이용해 지연할 수 있다.
```kotlin
object SingletonClass {
    val sampleString by lazy{ "Sample String" }
}
```

#원시 타입(primitive type)

- 코틀린은 원시 타입(primitive type)과 래퍼 타입(wrapper type)을 따로 구분하지 않습니다.  
즉, 자바처럼 Integer와 int로 구분하지 않고 Int 하나만 존재하는 형태입니다.
- 