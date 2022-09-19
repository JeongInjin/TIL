#Object Mother

- 테스트코드 작성시 클래스 인스턴스의 값을 하드코딩식으로 넣어주면서 작성 중이였다.
- 요건 정의가 늘어남에 따라, 클래스안에 생성자가 추가되고,
- 수많은 테스트코드의 클래스 생성시 에러가 발생할 여지가 생김.
- 그로인해 알게된 Object Mother
```kotlin
//기존 인스턴스 생성방식
bookRepository.save(Book("어린왕자"))
//변경 후
bookRepository.save(Book.fixture("어린왕자"))

@Entity
class Book(
    val name: String,

    val type: String,

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    val id: Long? = null,
) {

    init {
        if (name.isBlank()) {
            throw IllegalArgumentException("이름은 비어 있을 수 없습니다.")
        }
    }

    companion object {
        fun fixture(
            name: String = "책 이름",
            type: String = "COMPUTER",
            id: Long? = null,
        ): Book {
            return Book(
                name = name,
                type = type,
                id = id,
            )
        }
    }
}
```
- 이러한 패턴을 만들어주는 라이브러리가 있는것 같다 추후, 찾아보고 적용해 봐야할듯 하다.

