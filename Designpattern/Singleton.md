# **싱글톤(Singleton)**

## **싱글톤(Singleton)이란?**

- 클래스의 객체를 하나만 만들어야 하는 경우 사용한다. ( 프린터, 점수기록표 등 )
- 클래스 내에서 인스턴스가 단 하나뿐임을 보장하므로, 프로그램 전역에서 해당 클래스의 인스턴스를 바로 얻을 수 있고, 불필요한 메모리 낭비를 최소화한다.
- TCP Socket 통신에서 서버와 연결된 connect 객체에 주로 사용된다.

## **예시 코드**

### Eager initialization(사전 초기화)

```java
class Singleton {

    static final Singleton instance = new Singleton();

    private Singleton() {} // 생성자가 private 이라 new로 객체 생성이 불가능

    public Singleton getInstance() {
        return instance;
    }

}
```

- 클래스 로딩시에 인스턴스를 생성하는 방법이다.
- 인스턴스를 호출하지 않아도 무조건 생성하기에 메모리 효율이나 연산 효율은 상대적으로 낮다.

### Lazy initialization(사후 초기화)

```java
class Singleton {

		private static Singleton instance;

    private Singleton () {}

    public static Singleton getInstance() { // 인스턴스가 없으면 생성해서 반환
        if (instance == null) { instance = new Singleton ();}
        return instance;
    }

}
```

- 인스턴스가 요청될 때 생성되는 방식으로, 사전 초기화 방식보다 메모리와 연산량을 아낄 수 있다.
- **이중 객체 생성 문제**가 발생할 가능성이 높다. ()
- 인스턴스가 요청될 때 생성되므로 메모리와 연산량을 아낄 수 있다.

## **INDEX**

**이중 객체 생성 문제**

여러 스레드가 거의 동시에 싱글톤 인스턴스에 접근, 없는 것을 확인하고 생성하여 인스턴스를 생성해 싱글톤임에도 불구하고 객체가 중복되어 생성되는 문제
