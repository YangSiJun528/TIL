# Mark Down 란?

## **Mark Down 소개**

Markdown은 텍스트 기반의 마크업언어로 쉽게 쓰고 읽을 수 있으며 HTML로 변환 가능.  
특수기호와 문자를 이용한 간단한 문법을 사용하여 웹에서도 빠르게 컨텐츠 작성 및 직관적인 인식.

---

## **Mark Down 기본 문법**

### **헤더 Headers**

글머리: 1~6까지

```
# This is a H1
## This is a H2
### This is a H3
#### This is a H4
##### This is a H5
###### This is a H6
```

# This is a H1

## This is a H2

### This is a H3

#### This is a H4

##### This is a H5

###### This is a H6

### **BlockQuote**

```
> This is a first blockqute.
> >This is a second blockqute.
> > >This is a third blockqute.
```

> This is a first blockqute.
>
> > This is a second blockqute.
> >
> > > This is a third blockqute.

### **목록**

#### **1. 순서있는 목록(번호)**

1. 첫번째
2. 두번째
3. 세번째

```
1. 첫번째
3. 두번째
2. 세번째
```

어떤 수를 입력해도 내림차순으로 정의됨.

#### **● 순서없는 목록(글머리 기호: \_, +, - 지원)**

- 빨강
  - 녹색
    - 파랑

* 빨강
  - 녹색
    - 파랑

- 빨강
  - 녹색
    - 파랑

```
* 빨강
  * 녹색
    * 파랑

+ 빨강
  + 녹색
    + 파랑

- 빨강
  - 녹색
    - 파랑
```

### **코드**

#### **들여쓰기**

```
This is a normal paragraph:
    This is a code block.
    This is a code block.
end code block.
```

This is a normal paragraph:

    This is a code block.
    This is a code block.

end code block.

#### **코드블럭**

<pre>
  ```
  public class BootSpringBootApplication {
    public static void main(String[] args) {
      System.out.println("Hello, Honeymon");
    }
  }
  ```
</pre>

```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```

깃헙에서는 코드블럭코드("```")시작점에 언어를 선언해서 문법강조가 가능함.

<pre>
  ```java
  public class BootSpringBootApplication {
    public static void main(String[] args) {
      System.out.println("Hello, Honeymon");
    }
  }
  ```
</pre>

```java
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```

### **수평선**

```
* * *
***
- - -
---
```

---

모두 동일한 결과가 나온다.

### **링크**

#### **외부링크**

```
사용문법: [Title](link)
적용예: [Google](https://google.com, "google link")
```

[Google](https://google.com, "google link"

#### **자동연결**

```
- 외부링크: <http://example.com/>
- 이메일링크: <address@example.com>
```

외부링크: http://example.com/  
이메일링크: address@example.com

### **강조**

```
*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
~~cancelline~~
```

_single asterisks_  
_single underscores_  
**double asterisks**  
**double underscores**  
~~cancelline~~

### **이미지**

```
![Alt(이미지 깨질때) text](이미지 주소 "호버 택스트")
![Alt text](/path/to/img.jpg "Optional title")
```

![Alt(이미지 깨질때) text](./img.png "호버 택스트")

사이즈 조절 기능은 없기 때문에 `<img width="" height=""></img>` 를 이용한다

```
<img src="./img.png" width="300px" height="300px" alt="Daisy"></img>
```

<img src="./img.png" width="300px" height="300px" alt="Daisy"></img>

### 줄바꿈

3칸 이상 띄어쓰기를 하면 줄이 바뀐다.

```
* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다.
이렇게
```

줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다.  
이렇게
