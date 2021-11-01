# **전체 구조** (package 기준)

![Whole Structure](./img/structure.png "Whole Structure")

## **controller(web)**

- **기능**
  - 해당 요청 url에 따라 적절한 view와 mapping 처리
  - @Autowired Service를 통해 service의 method를 이용
  - 적절한 ResponseEntity(DTO)를 body에 담아 Client에 반환

#### **예시 1**

```java
  @Controller
  @RequestMapping("/")
  public class HomeController {
    @GetMapping
    public String home(HttpSession session) {
        if (!SessionUtil.getUser(session).isPresent()) {
            return "login";
        }
        return "index";
    }
}
```

> ❓ @Controller  
> API와 view를 동시에 사용하는 경우에 사용  
> 대신 API 서비스로 사용하는 경우는 @ResponseBody를 사용하여 객체를 반환한다.  
> view(화면) return이 주목적

#### **예시 2**

```java
  @RestController
  @RequestMapping("/api/users")
  public class ApiUserController {
    @Autowired
    private UserService userService;
    @PostMapping("/login")
    public ResponseEntity login(@RequestBody @Valid LoginDto loginDto, HttpSession session) {
        SessionUtil.setUser(session, userService.login(loginDto));
        return new ResponseEntity(HttpStatus.OK);
    }
  }
```

> ❓ @RestController
> view가 필요없는 API만 지원하는 서비스에서 사용 (Spring 4.0.1부터 제공)  
> @RequestMapping 메서드가 기본적으로 @ResponseBody 의미를 가정한다.  
> data(json, xml 등) return이 주목적: return ResponseEntity  
> 즉, @RestController = @Controller + @ResponseBody

## **service**

- **기능**
  - @Autowired Repository를 통해 repository의 method를 이용
  - 적절한 Business Logic을 처리한다.
  - DAO로 DB에 접근하고 DTO로 데이터를 전달받은 다음, 비지니스 로직을 처리해 적절한 데이터를 반환한다.

#### **예시**

```java
  @Service
  public class UserService {
    @Autowired
    private UserRepository userRepository;
    @Resource(name = "bCryptPasswordEncoder")
    private PasswordEncoder bCryptPasswordEncoder;
    @Autowired
    private MessageSourceAccessor msa;
    public User save(UserDto userDto) {
        if (isExistUser(userDto.getEmail())) {
            throw new UserDuplicatedException(msa.getMessage("email.duplicate.message"));
        }
        return userRepository.save(userDto.toEntityWithPasswordEncode(bCryptPasswordEncoder);
    }
  }
```

## **repository(dao)**

- **기능**

  - 실제로 DB에 접근하는 객체이다.
  - Service와 DB를 연결하는 고리의 역할을 한다.
  - SQL를 사용(개발자가 직접 코딩)하여 DB에 접근한 후 적절한 CRUD API를 제공한다.

    - JPA 대부분의 기본적인 CRUD method를 제공하고 있다.
    - ```java
      extends JpaRepository<User, Long>
      ```

#### **예시 (JPA의 경우)**

```java
  public interface UserRepository extends JpaRepository<User, Long> {
  }
```
