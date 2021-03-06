# **객체지향 설계 5원칙 SOLID**

## **SOLID란?**

SRP(단일 책임 원칙), OCP(개방-폐쇄 원칙), LSP(리스코프 치환 원칙), DIP(의존 역전 원칙), ISP(인터페이스 분리 원칙)을 말하며 앞자리를 따서 SOLID라고 한다.

시간이 지나도 유지 보수와 확장이 쉬운 소프트웨어를 만드는데 이 원칙들을 적용할 수 있다.

## **응집도와 결합도**

좋은 소프트웨어 설계를 위해서는 결합도(coupling)는 낮추고 응집도(cohesion)는 높여야 한다.

### **결합도**

모듈 (클래스, 기능) 간의 상호 의존 정도를 나타내는 지표로서 결합도가 낮으면 모듈간의 상호 의존성이 줄어들어서 객체의 재사용 및 유지보수가 유리합니다.

### **응집도**

하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져, 재사용 및 유지보수가 용이합니다.

## **SRP(Single Responsibility Principle)** **단일 책임 원칙**

한 모듈(클래스)은 단 하나의 책임만 가져야 한다.

## **OCP (Open/Closed Principle) 개방 폐쇄 원칙**

자신의 확장에는 열려 있고, 주변의 변화에 대해서는 닫혀 있어야 한다.

상위 클래스 또는 인터페이스를 중간에 둠으로써, 자신은 변화에 대해서는 폐쇄적이지만, 인터페이스는 외부의 변화에 대해서 확장을 개방해 줄 수 있다.

## **LSP (Liskov Substitution Principle) 리스코프 치환 원칙**

자식 클래스는 부모클래스에서 가능한 행위를 수행할 수 있어야 한다.

## **ISP (Interface Segregation Principle) 인터페이스 분리 원칙**

한 클래스는 자신이 사용하지 않는 인터페이스는 구현하지 말아야 한다.

하나의 일반적인 인터페이스보다는, 여러 개의 구체적인 인터페이스가 낫다.

즉, 자신이 사용하지 않는 기능(인터페이스)에는 영향을 받지 말아야 한다는 의미이다.

## **DIP (Dependency Inversion Principle) 의존 역전의 원칙**

추상화에 의존한다. 구체화에 의존하면 안된다.

변화하기 쉬운 것 보단 변화하기 어려운 것에 의존해야 한다.
