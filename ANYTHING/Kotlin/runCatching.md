#runCatching

- https://alkhwa-113.tistory.com/entry/TIL-Kotlin-runCatching-DTOEntity-%EC%9E%91%EC%84%B1-%ED%8C%81


```text
기본 문법

runCatching { } : 중괄호 안에 try 하고자 하는 구문을 작성
onSuccess { } : 위 runCatch 구문이 성공시 매핑할 구문을 작성. it 은 위 구문의 결과.
onFailure { } : 위 runCatch 구문이 실패시 매핑할 구문을 작성. it 은 위 구문에서 던진 Throwable 객체.
also { } : 기존 try-catch-finally 에서 finally 에서 작성하던 구문을 작성할 수 있음.

복잡한 상황

map { } : 성공한 값에 대해 한번더 가공이 가능. 여기서 예외가 발생하면 runCatching 구문 밖으로 예외를 던짐.
mapCatching { } : 성공한 값에 대해 한번더 가공이 가능. 여기서 예외가 발생하면 runCatching 구문 밖으로 예외를 던지지 않고, 그 예외를 담은 Result 객체 반환. 이후 onFailure 등으로 다시 잡아서 처리가능.
recover { } : 실패한 값에 대해 한번더 핸들링이 가능. 여기서 예외가 발생하면 runCatching 구문 밖으로 예외를 던짐.
recoverCatching { } :실패한 값에 대해 한번더 핸들링이 가능. 여기서 예외가 발생하면 runCatching 구문 밖으로 예외를 던지지 않고, 그 예외를 담은 Result 객체 반환. 이후 onFailure 등으로 다시 잡아서 처리가능.

 
runCatching 구문의 return 값이 필요할때

getOrNull() : 위에서 반환된 Result 객체가 성공객체 일 때 값 반환. 실패면 null
getOrDefault(~) : 위에서 반환된 Result 객체가 성공객체 일 때 값 반환. 실패면 뒤에 정의한 값 반환.
getOrThrow() : 위에서 반환된 Result 객체가 성공객체 일 때 값 반환. 실패면 Result 객체의 예외 throw.
getOrElse { } : 위에서 반환된 Result 객체가 성공객체 일 때 값 반환. 실패면 뒤에 정의한 구문 실행.
```