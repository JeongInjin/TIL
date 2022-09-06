#Coroutine

- 코루틴
  - 비동기로 여러 루틴을 실행하는 방법.
  - import kotlinx.coroutines.* 을 모두 import 하여야 한다.
  - 코루틴은 제어범위 및 실행범위를 지정할 수 있다. => 코루틴의 Scope 라 한다.
  - 코루틴 Scope
    - GlobalScope
      - 프로그램 어디서나 제어, 동작이 가능한 기본 범위
    - CoroutineScope
      - 특정한 목적의 Dispatcher 를 지정하여 제어 및 동작이 가능한 범위
    - CoroutineScope 를 만들때 적용가능한 Dispatcher
      - Dispatchers.Default => 기본적인 백그라운드동작
      - Dispatchers.IO => I/O 에 최적화 된 동작
      - Dispatchers.Main => 메인(UI) 스레드에서 동작
      - 이러 Dispatcher 들은 모든 플랫폼에서 지원되지는 않으니, 지원되는 플랫폼인지 확인 후 사용하자.
    
```kotlin
import kotlinx.coroutines.*

val scope = CoroutineScope(DisPatcher.Default)
val coroutineA = scope.launch{}
val coroutineB = scope.async{}
//생성된 스코프에서 launch, async 함수를 통해 새로운 스코프를 생성 시킬 수 있다.
```
  - launch vs async
    - 두개의 차이점은 반환값이 있는지의 여부
  - launch
    - 반환값이 없는 Job 객체 반환
  - async
    - 반환값이 있는 Deffered 객체 반환

```kotlin
launch {
    for(i in 1..10){
        println(i)
    }
}

async {
  var sum = 0
  for(i in 1..10){
    sum++
  }
  sum // <- 해당 값이 반환된다.
}
```

  - 기타옵션
    - delay: millisecond 단위로 루틴을 잠시 대기시키는 함수
    - Job.join(): Job 의 실행이 끝날때까지 대기하는 함수
    - Deferred.await(): Deferred 의 실행이 끝날때까지 대기하는함수
      - await() 는 Deferred 의 결과도 반환함
    - 이러한 옵션들은 코루틴 내부 또는 runBlocking{} 과 같은 루틴의 대기가 가능한 구문 안에서만 동작이 가능하다.
    - cancel(): 두가지 조건이 발생하며 코루틴을 중단시킬 수 있다.
      - 1: 코루틴 내부의 delay() 함수 또는 yield() 함수가 사용된 위치까지 수행된 뒤 종료됨
      - 2: cancel() 로 인해 속성인 isActive 가 false 가 되므로 이를 확인하여 수동 으로 종료함.
    - withTimeoutOrNull(): 제한시간 내에 수행되면 결과값을, 아닌 경우 null 을 반환한다.