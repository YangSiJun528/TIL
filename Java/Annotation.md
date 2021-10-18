# **Annotation이란?**

Annotation은 코드 사이에 주석처럼 쓰이면서 특별한 의미, 기능을 수행하도록 하는 기술로 프로그램에게 추가적인 정보를 제공해주는 메타 데이터이다.

```
예시 @Component, @Controller, @Repository, @Transactional, @Aspect
```

## **Annotation의 용도**

1. 컴파일러에게 코드 작성 문법 에러를 체크하도록 정보를 제공한다.
2. 컴파일러에게소프트웨어 개발툴이 빌드나 배치 시 코드를 자동으로 생성할 수 있도록 정보를 제공한다.
3. 런타임 시 특정 기능을 실행하도록 정보를 제공한다.

```
❗ Spring에서 제공되는 대부분의 Annotation은 3번, 런타임 시 특정 기능을 실행하도록 정보를 제공하는     용도로 사용되고 있다.
```

> 참고 : https://hirlawldo.tistory.com/43
