#Kotlin Delegation, Delegated Properties, class

- lateinit: 늦은 초기화
  - var(mutable) 변수 초기화를 의도적으로 지연시키는 방법
  - nullable 에서도 null 로 선언과 동시에 초기화 하지않고, init {} 에서 초기화 하지 않아도 된다.
  - 해당 property 를 사용하고자 할 때 초기화를 진행하고 바로 사용할 수 있음.
- by lazy: 게으른 초기화(프로퍼티 위임 초기화)
  - val(immutable) 상슈 property 에 지정
  - property 초기화를 위한 위임(delegated) 블록을 지정하여 맨 처음 참조 시 단 한번의 초기화를 진행하는 방법
  - 맨 처음 참조 시에 값을 얻게 되므로, 깔끔하게 null 처리가 전혀 불필요함.
