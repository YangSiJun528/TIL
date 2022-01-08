## 프록시(Proxy)란?

- 프록시(Proxy)는 대리인이라는 뜻으로, 무언가를 대신 처리한다는 의미입니다.

## 프록시(Proxy) 패턴

### 개념

- 프록시 패턴은 Proxy 객체를 통해 기본 객체에 접근하는 패턴이다.
- Proxy는 기본 객체를 Client 대신 접근해 처리(캐싱, 간단한 처리)해주고 Client는 Proxy를 통하여 결과를 받는다.
- 개방폐쇄 원칙(OCP)와 의존역전 원칙(DIP)을 따른다.

### 장점

- 기본 객체의 리소스가 무거운 경우, 프록시 객체에서 간단한 처리를 하거나 기본 객체를 캐싱 처리함으로써 부하를 줄일 수 있다.
- 기본 객체에 대한 수정 없이, 클라이언트와 기본 객체 사이에 일련의 로직을 프록시 객체를 통해 넣을 수 있다.
- 프록시는 기본 객체와 요청 사이에 있기 때문에, 일종의 방패(보안)의 역할도 한다.

### 단점

- 프록시 객체가 중간에 껴있기 때문에, 간혹 응답이 느려질 수 있다.

### 사용되는 방식

- **Virtual Proxy :** 프록시 클래스에서 자잘한 작업들을 처리, 주체 클래스가 필요한 상황에만 사용되도록 구현합니다.
- **Protection Proxy** : 프록시 클래스에서 주체 클래스에 대한 접근을 제어합니다.
- **Remote Proxy** : 프록시 클래스에서 원격 객체(주체 클래스, 다른 주소에 존재하는)에 대한 접근을 제어합니다**.**

## 구조

![proxy.png](./img/proxy.png)

- **Subject**
  - Proxy 와 RealSubject 가 구현해야하는 인터페이스
  - 두 객체를 동일하게 다루기 위해 존재
- **Proxy**
  - RealSubect 와 Client 요청 사이에 존재하는 객체
  - Subject 를 구현함으로써 클라이언트는 RealSubject 사용하는 것과 별 차이가 없어야 한다.
- **RealSubject**
  - 실질적으로 요청에 대해 주된 기능을 수행하는 객체
  - Proxy 객체는 내부적으로 이 객체를 로직에 맞게 사용한다. (위임)

## 예시

### **Image.java (Subject)**

```java
public interface Image {
   void displayImage();
}
```

### **Real_Image.java (RealSubject)**

```java
public class Real_Image implements Image {

    private String fileName;

    public Real_Image(String fileName) {
        this.fileName = fileName;
        loadFromDisk(fileName);
    }

    private void loadFromDisk(String fileName) {
        System.out.println("Loading " + fileName);
    }

    @Override
    public void displayImage() {
        System.out.println("Displaying " + fileName);
    }
}
```

### **Proxy_Image.java (Proxy)**

```java
public class Proxy_Image implements Image {
    private Real_Image realImage;
    private String fileName;

    public Proxy_Image(String fileName) {
        this.fileName = fileName;
    }

    @Override
    public void displayImage() { // 객체가 없는 경우 새 RealSubject 인스턴스를 생성(위임)
        if (realImage == null) {
            realImage = new Real_Image(fileName);
        }
        realImage.displayImage();
    }
}
```

### **Proxy_Main.java (Client)**

```java
public class Proxy_Main {
    public static void main(String[] args) {
        Image image = new Proxy_Image("test.png");

        image.displayImage();
				image.displayImage(); // 이 코드가 실행될 때 image의 정보가 Proxy에 저장되어서 RealSubject를 거치지 않아 복잡한 처리 없이 바로 실행된다.
    }
}
```
