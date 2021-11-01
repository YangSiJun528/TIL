# **DAO란?**

### **repository package**

- DAO는 Data Access Object의 약자다.
- DB에 접근하는 역할을 하는 객체를 말한다.
  - jdbc와 같은 것에서 db connection을 받아옴
  - DB와 통신
  - CRUD(생성, 읽기, 갱신, 삭제) 작업을 시행
  - DB 접근 로직과 비즈니스 로직을 분리하기 위해 사용
  -

## **예시 코드**

```java
public void printMyUserInfo(MyUser myuser){
	System.out.println("유저 번호는 : "+myuser.uidnum);
    System.out.println("유저 ID는 : "+myuser.uid);
    .
    .
}

public static void main(){
	MyUser myuser = new MyUser(1, "hello", "howru", "000-0000-0000", 50);
	public void printMyUserInfo(myuser);
}
```

# **DTO란?**

### **dto package**

- DTO는 Data Trasfer Object의 약자다.
- 계층간 데이터 교환을 위한 객체(Java Beans)이다.
  - DTO는 로직을 가지고 있지 않은 순수한 데이터임
  - 객체의 속성과 그 속성의 접근을 위한 getter 및 setter 메소드만을 가지고 있음
  - 하지만 DB에서 꺼낸 값을 임의로 변경할 필요가 없기 때문에 DTO클래스에는 setter가 없다. (대신 생성자에서 값을 할당한다.)

## **예시 코드**

```java
public class MyUser{
    private int uidnum;
    private String uid;
    private String upw;
    private String phonenum;
    private int age;

    public int getUidnum(){
    	return this.name;
    }
    public void setUidnum(int uidnum){
    	this.uid = uidnum;
    }
    // ... 중략
}
```

# Entity Class란

### **domain package**

- 실제 DB의 테이블과 매칭될 클래스
  - 즉, 테이블과 링크될 클래스임을 나타낸다.
  - Entity 클래스 또는 가장 Core한 클래스라고 부른다.
  - @Entity, @Column, @Id 등을 이용

## **Entity 클래스와 DTO 클래스를 분리하는 이유**

- View Layer와 DB Layer의 역할을 철저하게 분리하기 위해서
- 테이블과 매핑되는 Entity 클래스가 변경되면 여러 클래스에 영향을 끼치게 되는 반면 View와 통신하는 DTO 클래스(Request / Response 클래스)는 자주 변경되므로 분리해야 한다.
- Domain Model을 아무리 잘 설계했다고 해도 각 View 내에서 Domain Model의 getter만을 이용해서 원하는 정보를 표시하기가 어려운 경우가 종종 있다. 이런 경우 Domain Model 내에 Presentation을 위한 필드나 로직을 추가하게 되는데, 이러한 방식이 모델링의 순수성을 깨고 Domain Model 객체를 망가뜨리게 된다.

```java
@Entity
@Getter
@AllArgsConstructor
@NoArgsConstructor
@EqualsAndHashCode
@ToString
public class User implements Serializable {
  private static final long serialVersionUID = 7342736640368461848L;
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  @JsonProperty
  private Long id;
  @Column(nullable = false)
  @JsonProperty
  private String email;
  @Column(nullable = false)
  @JsonIgnore
  private String password;
  // @Override
  // public boolean equals(Object o) { ... }
  // @Override
  // public int hashCode() { ... }
  // @Override
  // public String toString() { ... }
```
