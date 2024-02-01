---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 27일차 (Spring)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "276"
tistoryPostUrl: https://yanacoding.tistory.com/276
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
## 자바 스프링 프레임워크를 통한 자바 객체 생성
### @Primary vs @Qualifier

### `@Primary`
- **목적:**
  - 여러 개의 빈(Bean) 중에서 주요한(primary) 빈을 지정하는 데 사용된다.
- **사용 시나리오:**
  - 여러 구현체 중에서 하나를 기본(primary)으로 선택하고자 할 때 사용된다.
- **사용 방법:**
  - `@Primary` 어노테이션을 해당 빈의 클래스나 메서드에 적용한다.
- **예시:**
  ```java
  @Component
  @Primary
  public class PrimaryBean implements MyInterface {
      // ...
  }
  ```

### `@Qualifier`
- **목적:**
  - 특정한 빈을 주입할 때 어떤 빈을 사용할지 지정하는 데 사용된다.
- **사용 시나리오:**
  - 여러 개의 동일한 타입의 빈이 존재하고 특정 빈을 주입하고자 할 때 사용된다.
- **사용 방법:**
  - `@Qualifier` 어노테이션을 주입 받는 필드, 생성자 매개변수, 또는 메서드 매개변수에 적용하고, 해당하는 빈의 이름을 지정한다.
- **예시:**
  ```java
  @Component
  public class ConsumerBean {
      private final MyInterface myBean;

      @Autowired
      public ConsumerBean(@Qualifier("specificBean") MyInterface myBean) {
          this.myBean = myBean;
      }
      // ...
  }
  ```

### 결론
- `@Primary`은 여러 구현체 중에서 기본(primary)으로 사용할 빈을 지정하는 데에 사용된다.
- `@Qualifier`는 여러 동일한 타입의 빈 중에서 특정한 빈을 주입할 때 사용된다.
- 두 어노테이션은 함께 사용될 수도 있다. `@Primary`로 주요 빈을 지정하고, `@Qualifier`를 통해 특정 빈을 명시적으로 선택할 수 있다.
### @Component vs @Bean
### `@Component`
- **목적:**
  - 클래스를 Spring의 빈으로 등록하기 위해 사용된다.
- **사용 시나리오:**
  - 주로 개발자가 작성한 클래스를 빈으로 등록하고자 할 때 사용된다.
- **사용 방법:**
  - `@Component` 어노테이션을 클래스에 적용한다.
- **예시:**
  ```java
  @Component
  public class MyComponent {
      // ...
  }
  ```

### `@Bean`
- **목적:**
  - 메서드를 통해 직접 빈을 정의하고 등록하기 위해 사용된다.
- **사용 시나리오:**
  - 개발자가 직접 메서드를 통해 빈을 정의하고 구성하고자 할 때 사용된다.
- **사용 방법:**
  - `@Bean` 어노테이션을 메서드에 적용한다. 해당 메서드가 반환하는 객체가 빈으로 등록된다.
- **예시:**
  ```java
  @Configuration
  public class MyConfiguration {

      @Bean
      public MyBean myBean() {
          return new MyBean();
      }
  }
  ```

### 공통점
- 둘 다 Spring에서 IoC 컨테이너에 빈을 등록하는 역할을 한다.

### 차이점
- `@Component`는 클래스에 적용되며, 해당 클래스의 객체가 빈으로 등록된다.
- `@Bean`은 메서드에 적용되며, 메서드가 반환하는 객체가 빈으로 등록된다. 일반적으로 `@Configuration` 어노테이션이 적용된 클래스에서 사용된다.

### 어떤 것을 사용해야 할까?
- `@Component`는 주로 외부 라이브러리나 프레임워크 등을 Spring 컨테이너에서 관리하고자 할 때 사용된다.
- `@Bean`은 주로 개발자가 직접 작성한 클래스의 빈을 등록하고자 할 때 사용되며, 특히 Java 기반의 Configuration 클래스에서 자주 활용된다.

### 결론
- `@Component`는 클래스 수준에서 사용되며, 클래스를 빈으로 등록한다.
- `@Bean`은 메서드 수준에서 사용되며, 메서드의 반환값을 빈으로 등록한다. 주로 Configuration 클래스에서 활용된다.

## 자바 스프링 프레임워크 고급 기능 알아보기
### Prototype vs Singleton(스프링 프레임워크 Bean 유효 범위 비교)
Spring Framework에서 빈(Bean)의 유효 범위(scope)에는 주로 "prototype"과 "singleton"이라는 두 가지가 사용됨.
### Prototype Scope
- **목적:**
  - 빈을 요청할 때마다 새로운 인스턴스를 생성하여 반환한다.
- **사용 시나리오:**
  - 매 요청마다 새로운 객체가 필요한 경우 사용된다.
  - 상태를 가지고 있어서는 안 되거나, 상태를 공유하면 안 되는 경우에 유용하다.
- **설정 방법:**
  - `@Scope("prototype")` 어노테이션을 클래스에 적용하거나 XML 설정에서 `<bean>` 태그에 `scope="prototype"`을 추가한다.

```java
@Component
@Scope("prototype")
public class MyPrototypeBean {
    // ...
}
```

### Singleton Scope
- **목적:**
  - 컨테이너 당 하나의 빈 인스턴스만 생성하고, 이를 계속해서 재사용한다.
- **사용 시나리오:**
  - 여러 곳에서 같은 객체를 공유해야 하는 경우 사용된다.
  - 상태를 가진 빈을 사용하는 경우, 해당 상태를 여러 곳에서 공유해야 할 때 유용하다.
- **설정 방법:**
  - 기본적으로 스프링 빈은 싱글톤 스코프이기 때문에 별도의 설정이 필요하지 않다. 단, 명시적으로 `@Scope("singleton")`을 사용할 수 있다.

```java
@Component
public class MySingletonBean {
    // ...
}
```

### 차이점
1. **인스턴스 생성 방식:**
   - **Prototype:** 매 요청마다 새로운 인스턴스를 생성한다.
   - **Singleton:** 컨테이너 당 하나의 인스턴스를 생성하고 재사용한다.

2. **상태 관리:**
   - **Prototype:** 상태를 가지고 있을 수 있고, 여러 클라이언트 간에 상태가 공유되지 않는다.
   - **Singleton:** 상태를 가질 수 있으며, 여러 클라이언트 간에 상태가 공유된다.

3. **메모리 사용:**
   - **Prototype:** 매 요청마다 새로운 인스턴스를 생성하므로 메모리 사용이 높을 수 있다.
   - **Singleton:** 하나의 인스턴스를 계속해서 재사용하므로 메모리 사용이 상대적으로 적다.

### 어떤 것을 사용해야 할까?
- **일반적으로는 Singleton을 사용하는 것이 권장됩니다.** 상태를 가지는 빈이나 공유해야 하는 리소스가 있을 때 효과적이며, 메모리 사용을 절약할 수 있습니다.
- **Prototype은 특별한 상황에서만 사용되어야 합니다.** 예를 들어, 매 요청마다 완전히 새로운 객체가 필요한 경우에 사용됩니다. 다만, 이 경우 메모리 사용이 증가할 수 있으므로 주의가 필요합니다.
## `@PostConstruct` and `@PreDestroy`

### `@PostConstruct`
- **목적:**
  - 빈이 초기화된 후에 실행할 메서드를 지정한다.
- **사용 시점:**
  - 빈이 생성된 후 초기화 작업을 수행해야 할 때 사용된다.
  - 의존성 주입 후 초기화를 해야하는 경우 유용하다.
- **사용 방법:**
  - `@PostConstruct` 어노테이션이 적용된 메서드를 선언한다.
- **예시:**
  ```java
  @Component
  public class MyBean {

      @PostConstruct
      public void init() {
          // 초기화 작업 수행
      }
  }
  ```

### `@PreDestroy`
- **목적:**
  - 빈이 소멸되기 전에 실행할 메서드를 지정한다.
- **사용 시점:**
  - 빈이 소멸되기 직전에 정리 작업을 수행해야 할 때 사용된다.
- **사용 방법:**
  - `@PreDestroy` 어노테이션이 적용된 메서드를 선언한다.
- **예시:**
  ```java
  @Component
  public class MyBean {

      @PreDestroy
      public void cleanup() {
          // 정리 작업 수행
      }
  }
  ```
### 결론
- `@PostConstruct`와 `@PreDestroy` 어노테이션은 각각 빈 초기화와 소멸 시의 동작을 지정할 때 사용된다.
## Java EE vs Jakarta EE

### Java EE (Java Platform, Enterprise Edition)
- **개요:**
  - Oracle에서 제공하는 기업용 자바 플랫폼.
  - 분산 컴퓨팅 및 웹 서비스를 개발하기 위한 API와 라이브러리를 제공한다.
  - 자바 EE 플랫폼은 Servlet, JSP, EJB 등의 기술을 포함한다.

### Jakarta EE (formerly Java EE)
- **개요:**
  - 자바 EE의 기술 스택을 Eclipse Foundation으로 이전하면서, Jakarta EE로 이름이 변경되었다.
  - Oracle은 자바 EE의 상표 및 관리 권한을 Eclipse Foundation에 이전하면서 이러한 변경이 이루어졌다.
  - Jakarta EE는 기업용 자바 애플리케이션을 개발하기 위한 업계 표준 플랫폼이다.

### 차이점
- **이름 및 브랜드:** Jakarta EE는 Oracle의 Java EE의 이후 이름이자 브랜드로 사용된다.
- **라이선스 및 관리:** Jakarta EE는 Eclipse Foundation에서 라이선스 및 관리되며, 오픈 소스 커뮤니티에 의해 주도된다.
- **API 및 스펙:** Jakarta EE는 Java EE의 기술 스택을 계승하면서, 지속적으로 새로운 기술과 업데이트가 이루어진다.

### 결론
- Jakarta EE는 Java EE의 후속이자 업데이트된 버전으로, 자바 기업 애플리케이션 개발에 사용되는 표준 플랫폼이다.

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 