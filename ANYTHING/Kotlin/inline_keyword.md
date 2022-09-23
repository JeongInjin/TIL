#inline function

참고: https://sabarada.tistory.com/176

- 람다식을 사용했을 때 무의미한 객체 생성을 예방
  - 인라인 함수를 사용한다면 람다식을 사용했을 때 무의미한 객체 생성을 막을 수 있습니다. 무슨 의미일까요? 이를 이해하기 위해서는 kotlin의 람다식이 컴파일될때 어떻게 변하는지를 확인해봐야합니다. 아래의 예제를 보도록 하겠습니다. 아래의 코드는 함수를 파라미터로 받고 특정한 일을한 후 해당 함수를 호출하는 코드입니다.
```kotlin
fun doSomethingElse(lambda: () -> Unit) {
    println("Doing something else")
    lambda()
}
```

- 이 코드를 컴파일하면 아래와 같은 java 파일이 됩니다. Functional Interface인 Function 객체를 파라미터로 받고 invoke 메서드를 실행합니다.

```kotlin
public static final void doSomethingElse(Function0 lambda) {
    System.out.println("Doing something else");
    lambda.invoke();
}
```

- 그렇다면 위의 함수를 사용하기 위해서는 아래처럼 코드를 작성할 수 있습니다. 아래의 코틀린 코드를 보도록 하겠습니다. doSomethingElse 함수를 호출하며 파라미터로 { println("Inside lambda") } 람다식을 넣었습니다.
```kotlin
fun doSomething() {
    println("Before lambda")
    doSomethingElse {
        println("Inside lambda")
    }
    println("After lambda")
}
```

- 그렇다면 이런 코틀린 코드는 컴파일되서 어떤 자바코드를 가지게 될까요? 바로 아래와 같은 코드가 나오게 됩니다. 아래 코드의 문제점이 무엇일까요? 눈치채신 분들도 있으시겠지만 doSomethingElse의 파라미터로 새로운 객체를 생성하여 넘겨준다는 것입니다. 이 객체는 doSomething이라는 메서드를 호출할 때마다 새로이 만들어집니다. 이는 무의미하게 새로운 객체를 매번 생성하는 것으로 보입니다.
```kotlin
public static final void doSomething() {
    System.out.println("Before lambda");
    doSomethingElse(new Function() {
            public final void invoke() {
            System.out.println("Inside lambda");
        }
    });
    System.out.println("After lambda");
}
```
- 이러한 문제점을 해결해주는 것이 바로 인라인(inline) 함수입니다. 인라인 함수를 사용하게 되면 코드는 객체를 항상 새로 만드는것이 아니라 해당 함수의 내용을 호출한 함수에 넣는 방식으로 컴파일 코드를 작성하게 됩니다. 아래의 예제코드를 보겠습니다. 기존의 코틀린 코드와 같지만 앞에 inline 키워드가 붙었습니다.

```kotlin
inline fun doSomethingElse(lambda: () -> Unit) {
    println("Doing something else")
    lambda()
}
```
- 사용하는 곳을 컴파일한 코드를 보도록 하겠습니다. Function 객체를 항상 호출했으나 이제는 내부에서 사용되는 2개의 함수가 내부 코드로 변환되어 사용되는것을 알 수 있었습니다. 이렇게 무의미하게 Function 객체를 항상 만들어내는 것이 없어졌습니다.

```kotlin
public static final void doSomething() {
    System.out.println("Before lambda");
    System.out.println("Doing something else");
    System.out.println("Inside lambda");
    System.out.println("After lambda");
}
```
- 람다식에 로컬 변수 사용
  - 위의 경우에 이어서 로컬 변수를 람다에서 사용한다면 어떻게 컴파일 되는지 알아보도록 하겠습니다. 많은 경우 지역(local) 변수를 람다식에 바로 대입해서 사용하곤 합니다. 아래의 코드와 같이 말이죠. 그런데 우리는 위에서 자바로 컴파일 될때 람다식이 Fnctional 객체로 변경되는것을 확인했습니다. 그렇다면 이렇게 사용한다면 내부에서는 컴파일 될까요 ?
```kotlin
fun doSomething() {
    val greetings = "Hello"                // Local variable
    doSomethingElse {
        println("$greetings from lambda")  // Variable capture
    }
}
```
- 컴파일 된 코드는 아래와 같습니다. 람다식에서 사용하는 지역 변수는 아래와 같이 Function 객체의 생성자의 변수로 들어가는 것을 확인할 수 있습니다.

```kotlin
public static final void doSomething() {
    String greetings = "Hello";
    doSomethingElse(new Function(greetings) {
            public final void invoke() {
            System.out.println(this.$greetings + " from lambda");
        }
    });
}
```
- 객체에 변수가 추가되었습니다. 즉, 객체의 메모리 사용량이 늘어났다는 것입니다. 이것을 볼때 이 경우 인라인 함수를 사용하면 좀 더 나은 성능을 보장할 수 있을 것이라는 사실을 알 수 있습니다.

