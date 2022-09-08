#Annotation

#@JvmStatic
  - static 변수의 get/set 함수를 자동으로 만들라는 의미.
  - 아래는 예제
```kotlin
class Bar {
    companion object {
        var barSize : Int = 0
    }
}
```
- companion object 는 자바의 static 과 다르다, 자바로 변환해보면 Bar class 에 batSize 는 선언이 되어있찌만 get/set 함수는 Bar.Companion 클래스에 등록되어있다.
```java
public final class Bar {
   private static int barSize;
   public static final class Companion {
      public final int getBarSize() {
         return Bar.barSize;
      }
      public final void setBarSize(int var1) {
         Bar.barSize = var1;
      }
   }
}
```
```kotlin
//@JvmStatic 은 Bar 밑에 get/set 함수사 생성되게끔 만든다.
class Bar {
  companion object {
    @JvmStatic var barSize : Int = 0
  }
}
```
- 자바로 변환하면
```java
public final class Bar {
   private static int barSize;
   public static final int getBarSize() {
      return barSize;
   }

   public static final void setBarSize(int var0) {
      barSize = var0;
   }

   public static final class Companion {
      public final int getBarSize() {
         return Bar.barSize;
      }
      public final void setBarSize(int var1) {
         Bar.barSize = var1;
      }
   }
}
```

#@JvmField
- get/set 을 생성하지 말라는 의미.