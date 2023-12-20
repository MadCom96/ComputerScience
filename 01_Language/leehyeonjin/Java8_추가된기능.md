# Java 8에서 추가된 기능

---

### Java 8에서 추가된 기능

1. Lambda 표현식 / 함수형 인터페이스 / Stream 등 함수형 프로그래밍 기능 추가.
2. 인터페이스에 Default Method와 Static Method를 추가하여 중복 코드 제거.
3. Optional 클래스를 통한 안전한 null 처리.
4. 날짜 관련 클래스 추가.
5. StringJoiner 를 통해 구분자, 접두사, 접미사를 붙여 String 연산 지원.

---

### **Lambda 함수 / 함수형 인터페이스 / Stream**

**Lamda 함수**

익명 함수를 단순하게 표현하는 방법.

특정 메소드 사용을 위한 일회용 객체를 만들지 않아도 되기 때문에 간단하게 작성 가능하고, 가독성이 증가함.

람다의 특징 :

- 함수의 이름이 필요없음.
- 일급객체로 사용됨.

> 💡 일급객체
>
> 함수를 값으로 사용할 수 있으며, 파라미터로 전달 및 변수에 대입하기와 같은 연산이 가능함.

람다의 장점 :

- 코드의 간결성.
- 지연연산 수행 → 불필요한 연산 최소화.
- 병렬처리 가능 → 멀티스레드를 활용하여 병렬처리 가능.

람다의 단점 :

- 람다 stream 사용시 단순 반복문의 성능이 저하됨.
- 불필요하게 너무 사용하게 되면 오히려 가독성을 떨어뜨릴 수 있음.
</br></br>

**함수형 인터페이스**

구현해야할 추상 메소드가 하나만 정의된 인터페이스.

@FuntionalInterface 애노테이션을 붙여 선언하며, 함수형 인터페이스에 메소드가 두 개 이상 선언되면 Javac에 의한 오류 발생.

```java
// 함수형 인터페이스와 람다 사용 예제
@FuntionalInterface
public interface Math {
	public int calc(int n1, int n2);
}

// 추상 메소드 구현 및 함수형 인터페이스 사용
Math plus = (n1, n2) -> n1 + n2; // 식이 하나라서 중괄호({}), return 생략
Math minus = (n1, n2) -> n1 + n2;
```

Java에서 지원하는 java.util.funtion 인터페이스

1. IntFunction<R>
- int 값의 인수를 받아들이고 결과를 생성하는 함수를 가짐.

```java
IntFunction sum = (x) -> x + 1;
System.out.println(sum.apply(1)); // 2
```

1. BinaryOperator<T>
- 동일한 유형의 두 피연산자에 대한 연산을 나타내며, 피연산자와 동일한 유형의 결과를 생성.

```java
BinaryOperator concat = (x, y) -> x + " " + y;
System.out.println(concat.apply("Hello", "World")); // Hello World
```
</br>

**Stream API**

Java에서 일련의 데이터 요소인 배열이나 컬렉션 등의 데이터를 처리하기 위한 api.

멀티스레드를 활용해서 병령로 연산을 수행가능하고, 내부 반복연산을 수행하기 때문에 코드가 매우 간결해짐.

```java
datas.stream().filter(x -> x < 2).count()
// stream() : 스트림 생성
// filter() : 중간 연산(스트림 변환) -> 연속에서 수행 가능
// count()  : 최종 연산(스트림 사용) -> 마지막에 단한번만 수행(지연연산)
```
