# **IoC (Inversion of Control)**

스프링의 3대 핵심 요소 중 하나이며 메소드나 객체의 생명 관리, 흐름 제어, 호출작업을 개발자가 결정하는 것이 아니라, 외부에서 결정되는 것을 IoC라고 합니다.

IoC가 적용된 구조에서는 외부 라이브러리의 코드가 프로그래머가 작성한 코드를 호출하는데, 설계 목적상 제어 반전의 목적은 아래와 같습니다.

- 작업을 구현하는 방식과 작업 수행 자체를 분리한다.
- 모듈을 제작할 때, 모듈과 외부 프로그램의 결합에 대해 고민할 필요 없이 모듈의 목적에 집중할 수 있다.
- 다른 시스템이 어떻게 동작할지에 대해 고민할 필요 없이, 미리 정해진 협약대로만 동작하게 하면 된다.

## **IoC 예시**

아래 그림은 기존의 객체 생성 방식입니다. 클래스 내부에 new 연산자를 이용하여 객체를 생성하였고 생명주기를 관리하였습니다.

Spring에서는 오른쪽 그림의 방식으로 객체를 생성합니다. 외부에서 객체를 생성하고 생성자/수정자 방식을 이용하여 객체를 주입하는 방식을 채택하였습니다.

![IoC_Ex](./img/IoC.PNG)

# **DI(Dependency Injection - 의존성 주입)**

IoC가 일어날 때 스프링이 내부에 있는 객체들간의 관계를 관리할 때 사용하는 기법이다.

DI는 클래스타입이 고정되어 있지 않고 인터페이스 타입의 파라미터를 통해 다이나믹하게 구현 클래스를 결정해서 제공 받을수 있어야 한다.

자바에서는 일반적으로 인터페이스를 이용해서 의존적인 객체의 관계를 최대한 유연하게 처리할 수 있도록 한다.

DI는 말 그대로 의존적인 객체를 직접 생성하거나 제어하는 것이 아니라**,** 특정 객체에 필요한 객체를 외부에서 결정해서 연결시키는 것을 의미한다.

즉, 우리는 클래스의 기능을 추상적으로 묶어둔 인터페이스를 갖다 쓰면 되는 것이다. 나머지는 스프링에서 객체를 주입해주기 때문이다. 따라서 이러한 의존성 주입으로 인해 모듈 간의 결합도가 낮아지고 유연성이 높아진다.