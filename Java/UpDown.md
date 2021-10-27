# UpCating / DownCating

```java
package interest;

class SuperClass {
  public void printSup() {
		System.out.println("부모 호출1");
  }
  public void print() {
		System.out.println("부모 호출2");
  }
}

class SubClass extends SuperClas
    public void printSub() {
		System.out.println("자식 호출1");
  }
    public void print() {
  		System.out.println("자식 호출2");
    }
}

class No1 {
  public static void main(String[] args) {
	  SuperClass sup = new SubClass();
		// 부모타입으로 자식타입의 객체를 참조할 때는 묵시적으로 형변환이 일어난다.
	// UpCating
	  // 1. SubClass 생성
	  // 2. SubClass을 SuperClass로 형변환 해서 sup에 저장
	  System.out.println(sup.getClass().getName()); // interest.SubClass
	  sup.printSup();  // 부모 호출1
	  sup.print();  // 자식 호출2 -> 오버라이드 됨
	  // sup.printSub();  // 에러 : The method printSub() is undefined for the type SuperClass

	// DownCating

	  // 부모타입의 객체를 자식타입으로 참조하게 할때는 명시적으로 형변환 해주어 한다.
	  // 단 이렇게 형변환 할때에는 부모가 참조하는 인스턴스가 형변환 하려는 자식타입일 때만 가능하다.
	  // 예시 : SuperClass sup = new SubClass();
	  SubClass sub = (SubClass)sup;
	  sub.printSup();
	  sub.printSub();
	  sub.print();
  }
}
```
