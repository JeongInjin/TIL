#Collections

- 시퀀스(sequences)
  - sequences 의 여러 단계 처리는 전체 단계가 처리된 결과가 요구됐을 때에 실제 연산이 일어나며 느리게 처리된다.
  - sequence 는 각각 하나의 element 에 대해 모든 단계를 수행한다.
  - iterable 은 전체 collection 에 대해 각 단계의 수행을 완료하고, 다음 단계로 넘어간다.
  - 따라서 sequence 는 중간 단계의 결과에 대한 처리를 피할 수 있게 해주며, collection 전체 처리에 대한 수행 성능이 향상됨.
  - 하지만 크기가 작은 collection 이나 단순한 연산 동작에 대해서는 오히려 불필요한 오버헤드가 생길 수 있다.
  - 즉 적절하게 선택하자.


- 콜렉션 vs 시퀀스 비교
  - 콜렉션:
```kotlin
val list = listOf(1, 2, -3)   // [1, 2, -3] 생성
val maxOddSquare = list
    .map { it * it }          // [1, 4, 9] 생성
    .filter { it % 2 == 1 }   // [1, 9] 생성
    .max()
```
  - 시퀀스:
```kotlin
val list = listOf(1, 2, -3)   // [1, 2, -3] 생성
val maxOddSquare = list
    .asSequence()
    .map { it * it }
    .filter { it % 2 == 1 }
    .max()
```

---
```kotlin
fun main() {
    (1..10).asSequence()
	    .filter { print("F$it, "); it % 2 == 1}
        .map { print("M$it, "); it * 2}
        .first()
        // F1, M1

    println("")
 
    (1..10)
        .filter { print("F$it, "); it % 2 == 1}
        .map { print("M$it, "); it * 2}
        .first()
   		// F1, F2, F3, F4, F5, F6, F7, F8, F9, F10, M1, M3, M5, M7, M9,
}
```
으어어어..
- iterable 은 수평적 평가
- sequence 는 수직적 평가
- 라고 생각해야겠다. 머리아프다.

- 연산자 오버로딩과 기타 관례
  - list.add -> list += 1 식으로 가능.(이게 더 나은듯)
  - 이펙티브 코틀린 아이템1 16페이지를 살펴보면 add 는 구체적 리스트 구현 내부에 변경 가능 지점이 있어 적절한 동기화가 되어 있는지 확시랗게 알 수 없으므로 위험하다고 한다.
  - += 는 프로퍼티 자체가 변경 가능 지점이여서 멀티스레드 처리의 안정성이 더 좋다고 한다.
  - += 이런식으로 쓸 수 있는 이유는 코틀린이 관례를 따라서라는데 자세한건 아래 주소에 들어가서 살펴보자.
  - ex)plus -> + 도 쓸 수 있다. *미리 함수와 연결시켜 놓은듯.
  - https://jjunsu.tistory.com/41


