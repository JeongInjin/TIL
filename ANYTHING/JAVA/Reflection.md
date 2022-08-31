#Reflection
-https://codechacha.com/ko/reflection/
- Reflection
  - 구체적인 클래스 타입을 알지못해도, 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API
- 언제사용
  - 어떤 클래스를 사용할지 모르지만, 런타임 시점에 실행되고 있는 클래스를 가져와 실행해야 하는 경우
  - 변수의 값을 조건에 따라 다르게 사용해야하는 경우, 어플리케이션이 실행되고 나서 생성되는 클래스


```java
//생성자 찾기
//getDeclaredConstructor()를 이용해 클래스로부터 생성자를 가져올수 있다.
//찾는 class 가 없을시 classNotFount exception 이 발생한다.
Class clazz = Class.forName("Person");
Constructor constructor = clazz.getDeclaredConstructor();
```

```java
//Method 찾기

Class clazz = Person.class;
Method[] methodList = clazz.getDeclaredMethods();    
System.out.println(methods[0].invoke(clazz.newInstance())) // 27이 출력됨
```
```java
//Field 변경

Class clazz = Person.class;
Field[] field = clazz.getDeclaredFields();
System.out.println(field[0]);   // 출력 : int reflection_test.Person.age
```
```java
//필드 가져오기

Class clazz = Person.class;
Field[] field = clazz.getDeclaredFields();

Person person = new Person();
field[0].set(person, 17);
System.out.println(field[0].get(person));  // 17이 출력됨 
```