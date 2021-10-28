# **DAO란?**

- DAO는 Data Access Object의 약자다.
- DbB에 접근하는 역할을 하는 객체를 말한다.
  - jdbc와 같은 것에서 db connection을 받아옴
  - DB와 통신
  - CRUD(생성, 읽기, 갱신, 삭제) 작업을 시행
  - DB 접근 로직과 비즈니스 로직을 분리하기 위해 사용

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

> 내 유저 정보를 가지고 있는 클래스 변수를 선언하여 '묶음'으로써 정보를 전달한다.

# **DTO란?**

- DTO는 Data Trasfer Object의 약자다.
- 계층간 데이터 교환을 위한 객체(Java Beans)이다.
  - DTO는 로직을 가지고 있지 않은 순수한 데이터임
  - 객체의 속성과 그 속성의 접근을 위한 getter 및 setter 메소드만을 가지고 있음

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
