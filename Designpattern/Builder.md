# **빌더(Builder) 패턴**

## **빌더(Builder) 패턴이란?**

### **개념**

복합 객체의 생성 과정과 표현 방법을 분리하여 동일한 생성 절차에서 서로 다른 표현 결과를 만들 수 있게 하는 패턴이다.

간단히 **생성자 오버로딩** 이라고도 함

### **장점**

- API 같이 시간이 지날수록 매개변수가 많아지는 경우 유용하다.(유연성을 확보할 수 있음)
- 생성과 표현 코드를 분리한다
- 불변성을 확보할 수 있다.(추가적인 설정이 필요함, 빌더 패턴 자체로 불변성을 가지진 않는다.)

### **단점**

- 빌더 생성 비용이 크지는 않지만 성능에 민감한 상황에서는 문제가 될 수 있다.

## **구조**

![Builder-Structure.png](./img/Builder-Structure.png)

- Builder
  - Director가 요청하는 build 연산을 정의한다.
  - Director의 요청을 처리해 Product에 부품을 추가한다.
- Product
  - 생성하고자 하는 클래스
- Director
  - Product의 일부가 build될 때마다 Builder에 통보한다.
  - 생성이 완료된 클래스를 반환한다.
- ConcreteBuilder
  - Builder를 상속받아 필요한 표현을 override한다

## **예시**

### Product

```java
class Pizza {
	private String dough = "";
	private String sauce = "";
	private String topping = "";

	public void setDough(String dough) {
		this.dough = dough;
	}

	public void setSauce(String sauce) {
		this.sauce = sauce;
	}

	public void setTopping(String topping) {
		this.topping = topping;
	}
}
```

### Abstract Builder

```java
abstract class PizzaBuilder {
	protected Pizza pizza;

	public Pizza getPizza() {
		return pizza;
	}

	public void createNewPizzaProduct() {
		pizza = new Pizza();
	}

	public abstract void buildDough();

	public abstract void buildSauce();

	public abstract void buildTopping();
}
```

### ConcreteBuilder

```java
class HawaiianPizzaBuilder extends PizzaBuilder {
	public void buildDough() {
		pizza.setDough("cross");
	}

	public void buildSauce() {
		pizza.setSauce("mild");
	}

	public void buildTopping() {
		pizza.setTopping("ham+pineapple");
	}
}
```

```java
class SpicyPizzaBuilder extends PizzaBuilder {
	public void buildDough() {
		pizza.setDough("pan baked");
	}

	public void buildSauce() {
		pizza.setSauce("hot");
	}

	public void buildTopping() {
		pizza.setTopping("pepperoni+salami");
	}
```

### Director

```java
class Cook {
	private PizzaBuilder pizzaBuilder;

	public void setPizzaBuilder(PizzaBuilder pizzaBuilder) {
		this.pizzaBuilder = pizzaBuilder;
	}

	public Pizza getPizza() {
		return pizzaBuilder.getPizza();
	}

	public void constructPizza() {
		pizzaBuilder.createNewPizzaProduct();
		pizzaBuilder.buildDough();
		pizzaBuilder.buildSauce();
		pizzaBuilder.buildTopping();
	}
}
```

### Client

```java
public class BuilderExample {
	public static void main(String[] args) {
		Cook cook = new Cook();
		PizzaBuilder hawaiianPizzaBuilder = new HawaiianPizzaBuilder();
		PizzaBuilder spicyPizzaBuilder = new SpicyPizzaBuilder();

		cook.setPizzaBuilder(hawaiianPizzaBuilder);
		cook.constructPizza();

		Pizza pizza = cook.getPizza();
	}
}
```

## 더 간단한 빌더 패턴

```java
public class Car {
    // final 키워드를 써서 생성자를 통한 입력을 강요함
    private final String id, name;
    // 클래스 안에 스태틱 형태의 내부 클래스(inner class) 생성
    protected static class Builder {
        private String id;
        private String name;
        // id 입력값 받음: 리턴 타입을 Builder 타입으로 한 다음 this를 리턴
        public Builder id(String value) {
            id = value;
            return this;
        }
        // name 입력값 받음: 리턴 타입을 Builder 타입으로 한 다음 this를 리턴
        public Builder name(String value) {
            name = value;
            return this;
        }
        // 마지막에 build() 메소드를 실행하면 this가 리턴되도록 함
        public Car build() {
            return new Car(this);
        }
    }
    // 생성자를 private로 함
    // 외부에서는 접근할 수 없고 위의 Builder 클래스에서는 사용 가능
    private Car(Builder builder) {
        id = builder.id;
        name = builder.name;
    }

    // 빌더 소환: 외부에서 Car.builder() 형태로 접근 가능하게 스태틱 메소드로
    public static Builder builder() {
        return new Builder();
    }
    // Getter
    public String getId() {
        return id;
    }
    public String getName() {
        return name;
    }
}
```

### Client

```java
public class BuilderExample {
	public static void main(String[] args) {
		String id = "1";
		String name = "Charles";
		Car car1 = Car.builder()
		        .id(id)
		        .name(name)
		        .build();
	}
}
```

## **INDEX**
