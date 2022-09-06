#Design Pattern

- observer
```kotlin
fun main() {
	EventPrinter().start()
}

interface EventListener {
    fun onEvent(count: Int)
}

class Counter(var listener: EventListener) {
    fun count() {
        for(i in 1..100) {
            if(i % 5 == 0) listener.onEvent(i)
        }
    }
}

class EventPrinter: EventListener {
    override fun onEvent(count: Int) {
        println("${count} -")
    }
    fun start() {
        val counter = Counter(this)
        counter.count()
    }
}

//5 -
//10 -
//15 -
//20 -
//...
        
```
- 또는 https://pjh3749.tistory.com/266
```kotlin

fun main() {
	val injin = Injin()
    val sub1 = subscribe1()
    val sub2 = subscribe2()
    val sub3 = subscribe3()
    
    injin.subscribe(sub1)
    injin.subscribe(sub2)
    injin.subscribe(sub3)
    
    injin.eatFood()
    
    injin.unsubscribe(sub3)
    injin.run()
}

interface Coach {
    fun subscribe(crew: Crew)
    fun unsubscribe(crew: Crew)
    fun notifyCrew(msg: String)
}

interface Crew {
    fun updateMsg(msg: String)
}


class Injin: Coach {
    var crews = ArrayList<Crew>()

    fun eatFood() {
        println("인진이 밥을 먹는다.")
        notifyCrew("밥 먹었음")
    }

    fun run() {
        println("인진이 뛴다.")
        notifyCrew("뛰었음")
    }

    override fun subscribe(crew: Crew) {
        crews.add(crew)
    }

    override fun unsubscribe(crew: Crew) {
        crews.remove(crew)
    }

    override fun notifyCrew(msg: String) {
        for (crew in crews) crew.updateMsg(msg)
    }
}

class subscribe1 : Crew {
    override fun updateMsg(msg: String) {
        println("구독자1 수신: $msg")
    }
}
class subscribe2 : Crew {
    override fun updateMsg(msg: String) {
        println("구독자2 수신: $msg")
    }
}
class subscribe3 : Crew {
    override fun updateMsg(msg: String) {
        println("구독자3 수신: $msg")
    }
}
//인진이 밥을 먹는다.
//구독자1 수신: 밥 먹었음
//구독자2 수신: 밥 먹었음
//구독자3 수신: 밥 먹었음
//인진이 뛴다.
//구독자1 수신: 뛰었음
//구독자2 수신: 뛰었음
```

