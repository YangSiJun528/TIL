# **열거 타입(Enum)**

## **열거형(Enum)**

Enum은 서로 관련이 있는 상수들의 집합이다.

### 특징

- 서로 관련 있는 상수 값들을 모아 enum으로 구현하는 경우 유용하다.
- 데이터의 그룹화 및 관리에 용이하다.
- 클래스와 같은 문법 체계를 따른다.
- 클래스를 상수처럼 사용 할 수 있다.
- 상수 값과 같이 하나의 인스턴스가 생성되어 싱글톤 형태로 어플리케이션 전체에서 사용된다.
- 상속을 지원하지 않는다.
  - 모든 enum들은 내부적으로 `java.lang.enum` 클래스에 의해 상속되어 다른 클래스를 상속 받을 수 없다.
- 열거 상수를 적을 때는 관례로 대문자로 적는다. 만약 열거상수가 2개의 단어로 연결되어 있을 때는 `_` 로 연결한다. ex) START_DATE

## 예시

### 선언 방법

```java
enum Season { //class 외부에서 선언
    봄, 여름, 가을, 겨울
}

public class enum_ex {
	public enum Season { //class 내부에서 선언
        봄, 여름, 가을, 겨울
    }
}
```

### 사용 방법

```java
public class enum_ex {
    public enum Season {
	    봄, 여름, 가을, 겨울
    }

    public static void main(String[] args) {
        Season season = Season.봄;
        System.out.println(season);
        System.out.print(Season.여름);
    }
}
```

### **Enum 추가 속성과 생성자**

열거형 상수는 추가 속성을 부여할 수 있으며 추가 속성이 여러 개가 있을 시 생성자에 순서대로 각각의 타입으로 넣을 수 있다.

```java
public enum Color {

    RED("빨강",100), GREEN("초록",10), BLUE("파랑",30);

    private String koreName;
    private int pay;

    // 빨강, 100 순서대로 할당된다.
    private Color(String koreName, int pay){
        this.koreName = koreName;
        this.pay      = pay;
    }

    public void colorInfo(){
        System.out.println(koreName +"의 비용은 " + pay +"입니다.");
    }
}

Color.BLUE.colorInfo();
```

## Enum 내부 method

### values()

- Enum 클래스가 가지고 있는 모든 인스턴스를 배열에 담아 반환한다.

### valueOf()

- `String` 을 파라미터로 받아, 인자로 들어온 `String` 과 일치하는 상수 인스턴스가 존재하면 그 인스턴스를 반환한다.

### ordinal()

- Enum 클래스 내부에 있는 상수들의 Index 를 리턴하는 메소드이다.
- 0부터 인덱스가 시작하며 인덱스의 length 는 상수의 수 - 1 이다.
