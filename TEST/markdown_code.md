# markdown

TIL에 앞서 markdown test

This is an H1
=============

This is an H2
-------------



> This is a first blockqute.
>	> This is a second blockqute.
>	>	> This is a third blockqute.

  
# This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6


1. 첫번째
2. 두번째
3. 세번째

* 빨강
  * 녹색
    * 파랑

+ 빨강
  + 녹색
    + 파랑

- 빨강
  - 녹색
    - 파랑

* 1단계
  - 2단계
    + 3단계
      + 4단계

This is a normal paragraph:

    This is a code block.
    
end code block.

<pre>
<code>
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }

}
</code>
</pre>


```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```

```java
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, World");
  }
}
``` 

* * *

***

*****

- - -

---

---------------------------------------   

[link keyword][id]

[id]: URL "Optional Title here"


Link: [Google][googlelink]

[googlelink]: https://google.com "Go google"

*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
~~cancelline~~   

<img src="/path/to/img.jpg" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
<img src="/path/to/img.jpg" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img>

* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다. 
이렇게   

* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다.___\\ 띄어쓰기


이렇게  
강제개행 문법  
입니다.  
문자열 마지막에 공백을 두번 입력합니다.

__볼드체__  
**볼드체**

> If you can imagine it, you can achieve it; if you can dream it, you can become it.
당신이 상상을 할 수 있다면 그것을 이룰 수 있고, 당신이 꿈꿀 수 있다면 그 꿈대로 될 수 있다.