# **Lombok 이란?**

- 어노테이션 기반으로 기계적인 코드 작성을 자동화하여 가독성 및 유지보수성 향상에 도움을 주는 라이브러리이다.
- Lombok을 이용해 Getter, Setter, Equlas, ToString 등과 같은 다양한 코드를 자동완성 시킬 수 있다.

## **예시**

```java
public class User {
  private String name;
  private String id;
  private String password;

  public String getName() {
    return name;
  }

    public String setName(String name) {
    return this.name = name;
  }

    public String getId() {
    return id;
  }
  // ...중략
}
```

예시와 같은 코드에서 Lombok을 사용한다면

```java
@Getter
@Setter
public class User {
  private String name;
  private String id;
  private String password;
}
```

이처럼 확연히 줄어든 코드를 확인할 수 있다.

## **간략한 Lombok 기능 소개**

### **[ @Getter @Setter ]**

Lombok에서 가장 자주 활용하는 어노테이션이다.  
@Getter와 @Setter를 클래스 이름 위에 적용시키면 모든 변수들에 적용이 가능하고, 변수 이름 위에 적용시키면 해당 변수들만 적용 가능하다.

### **[ @AllArgsConstructor ]**

@AllArgsConstructor는 모든 변수를 사용하는 생성자를 자동완성 시켜주는 어노테이션이다.

### **[ @NoArgsConstructor ]**

@NoArgsConstructor는 어떠한 변수도 사용하지 않는 기본 생성자를 자동완성 시켜주는 어노테이션이다.

### **[ @RequiredArgsConstructor ]**

@RequiredArgsConstructor는 특정 변수만을 활용하는 생성자를 자동완성 시켜주는 어노테이션이다.  
생성자의 인자로 추가할 변수에 @NonNull 어노테이션을 붙여서 해당 변수를 생성자의 인자로 추가할 수 있다.  
또는 해당 변수를 final로 선언해도 의존성을 주입받을 수 있다.

### **[ @EqualsAndHashCode ]**

@EqualsAndHashCode 어노테이션은 클래스에 대한 equals 함수와 hashCode 함수를 자동으로 생성해준다.  
@RequiredArgsConstructor와 동일하게 @NonNull 어노테이션 또는 final 을 이용하여 추가할 수 았다.

### **[ @ToString ]**

@ToString 어노테이션을 활용하면 클래스의 변수들을 기반으로 ToString 메소드를 자동으로 완성시켜 준다.  
출력을 원하지 않는 변수에 @ToString.Exclude 어노테이션을 붙여주면 출력을 제외할 수 있다.

### **[ @Data ]**

@Data 어노테이션은 @ToString, @EqualsAndHashCode, @Getter, @Setter,@RequiredArgsConstructor를 자동완성 시켜준다.  
실무에서는 너무 무겁고 객체의 안정성을 지키기 위해 @Data의 활용을 지양한다.

### **[ @Builder ]**

@Builder 어노테이션은 해당 클래스의 객체의 생성에 Builder패턴을 적용시켜준다.  
모든 변수들에 대해 build하기를 원한다면 클래스 위에 @Builder를 붙이면 되지만, 특정 변수만을 build하기 원한다면 생성자를 작성하고 그 위에 @Builder 어노테이션을 붙여주면 된다.

### **[ @Delegate ]**

@Delegate 어노테이션은 한 객체의 메소드를 다른 객체로 위임시켜 준다.
