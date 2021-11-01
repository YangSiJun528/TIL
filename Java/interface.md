## **상수**

- 모든 변수는 상수로 변환 됨

```java
public static final
double PI = 3.14;
int ERROR = -999999999;
```

## **추상 메서드**

- 모든 선언된 메서드는 추상 메서드

```java
public abstract
```

## **디폴트 메서드 (자바 8이후)**

- 구현을 가지는 메서드, 인터페이스를 구현하는 클래스들에서 공통으로 사용할 수 있는 기본 메서드
- 인터페이스를 구현한 클래스의 인스턴스가 생성 되어야 사용 가능함

### **default 키워드 사용**

```java
default void description() {
	System.out.println("정수 계산기를 구현합니다.");
	myMethod();
}
구현 하는 클래스에서 재정의 할 수 있음
@Override
public void description() {
	System.out.println("CompleteCalc에서 재정의한 default 메서드");
	//super.description();
}
```

### **사용 이유**

> ...(중략) ... 바로 "하위 호환성"때문이다. 예를 들어 설명하자면, 여러분들이 만약 오픈 소스코드를 만들었다고 가정하자. 그 오픈소스가 엄청 유명해져서 전 세계 사람들이 다 사용하고 있는데, 인터페이스에 새로운 메소드를 만들어야 하는 상황이 발생했다. 자칫 잘못하면 내가 만든 오픈소스를 사용한 사람들은 전부 오류가 발생하고 수정을 해야 하는 일이 발생할 수도 있다. 이럴 때 사용하는 것이 바로 default 메소드다. (자바의 신 2권)

## **정적 메서드 (자바 8이후)**

- 인스턴스 생성과 상관 없이 인터페이스 타입으로 사용할 수 있는 메서드

```java
static int total(int[] arr) {
	int total = 0;

	for(int i: arr) {
		total += i;
	}
	mystaticMethod();
	return total;
}
```

> 인터페이스에서 정의한 static메소드는 반드시 인터페이스명.메소드 형식으로 호출해야한다.

## **private 메서드 (자바 9이후)상수**

- 인터페이스를 구현한 클래스에서 사용하거나 재정의 할 수 없음

- 인터페이스 내부에서만 사용하기 위해 구현하는 메서드

- default 메서드나 static 메서드에서 사용함

```java
private void myMethod() {
	System.out.println("private method");
}

private static void mystaticMethod() {
	System.out.println("private static method");
}
```
