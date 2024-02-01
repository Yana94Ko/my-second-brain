---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 26일차 (JAVA, Spring)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "265"
tistoryPostUrl: https://yanacoding.tistory.com/265
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
## 자바 Record - JAVA 16
클래스의 특별한 한 종류.
#### class 와의 차이점
1. 클래스를 상속 받을 수 없음
2. 인스턴스 필드 선언 불가(정적 필드 선언 가능)
3. 추상으로 선언 불가하며, 암시적 final로 선언됨
4. 클래스 내에서 레코드를 선언할 수 있다. 중첩된 레코드는 암시적으로 static으로 선언된다.
5. 제네릭 레코드를 만들 수 있다.
6. 레코드는 클래스처럼 인터페이스를 구현할 수 있다.
7. new 키워드를 사용하여 레코드를 인스턴스화할 수 있다.
8. 레코드의 본문(body)에는 정적 필드, 정적 메서드, 정적 이니셜라이저, 생성자, 인스턴스 메서드, 중첩 타입(클래스, 인터페이스, 열거형 등)을 선언할 수 있다.
9. 레코드나 레코드의 각 컴포넌트에 애노테이션을 달 수 있다.
#### record 이전의 코드(DTO)
```java
public class BookDto {  
    private String title;  
    private String author;  
    private String isbn;  
    private String publisher;  

    public String getTitle() {  
        return title;  
    }  

    public String getAuthor() {  
        return author;  
    }
    // ... 수많은 코드 ...
    @Override  
    public int hashCode() {  
        return Objects.hash(title, author, isbn, publisher);  
    }
}
```
#### record 활용 코드(DTO)
```java
public record BookDto(
	String title, 
	String author, 
	String isbn, 
	String publisher) { 
}
```
## 추가적으로 생각해보면 좋을 것
"record를 사용한 DTO 생성과, innerClass를 사용한 DTO 생성의 차이점과 각각의 강점"

## Spring Boot vs Spring vs Spring MVC
## Spring
- **개요:** 
  - 자바 기반의 프레임워크로, 기업 환경에서 대규모 응용 프로그램을 개발하기 위한 종합적인 솔루션을 제공한다.
  - 모듈화, DI (의존성 주입), AOP (관점 지향 프로그래밍) 등을 지원하여 유연하고 확장 가능한 애플리케이션을 만들 수 있다.

- **Spring Framework 구성요소:**
  - **Core Container:** IoC 컨테이너, 빈 팩토리 등이 포함되어 있으며, DI를 지원한다.
  - **Data Access/Integration:** JDBC, ORM 등 데이터 액세스 및 통합을 위한 모듈 제공.
  - **Web:** 웹 애플리케이션 개발을 위한 모듈로 Spring MVC 포함.
  - **AOP (Aspect-Oriented Programming):** 관점 지향 프로그래밍을 지원하는 모듈.
  - **Instrumentation:** 클래스 로딩 및 변경을 위한 인스트루멘테이션 지원.
  - **Messaging:** 메시지 기반의 애플리케이션을 구축하기 위한 모듈.

## Spring MVC
- **개요:**
  - Spring에서 제공하는 웹 애플리케이션 개발을 위한 프레임워크.
  - 모델-뷰-컨트롤러 (MVC) 아키텍처를 기반으로 한다.

- **특징:**
  - **MVC 아키텍처:** 모델(데이터), 뷰(사용자 인터페이스), 컨트롤러(로직 처리)를 분리하여 유지보수 및 확장성을 향상시킨다.
  - **HTTP 및 RESTful 지원:** 다양한 HTTP 메서드 및 RESTful 웹 서비스를 구현할 수 있다.
  - **빠른 개발 및 유연성:** 애노테이션을 사용하여 간단한 설정으로 빠르게 웹 애플리케이션을 개발할 수 있다.

## Spring Boot
- **개요:**
  - Spring 기반의 애플리케이션을 빠르게 개발하고 실행할 수 있도록 도와주는 프로젝트.
  - 기본 설정이 자동화되어 있어 별도의 설정 없이도 간단한 명령어로 애플리케이션을 실행할 수 있다.

- **특징:**
  - **스타터 (Starter) 패키지:** 특정 기술 스택을 사용하는 데 필요한 모든 종속성이 사전 구성된 패키지를 제공하여 개발자가 간편하게 프로젝트를 시작할 수 있다.
  - **자동 구성 (Auto Configuration):** 클래스패스 내에서 라이브러리를 감지하고 자동으로 설정하여 빠르게 개발할 수 있도록 도와준다.
  - **장애 내구성 (Production-Ready):** 기본적인 보안, 성능, 모니터링 등의 기능을 내장하여 생산 환경에 적합하게 만들어진다.

## 결론
- **Spring:** 기업 환경에서 다양한 기능을 제공하는 전체적인 프레임워크.
- **Spring MVC:** 웹 애플리케이션을 개발하기 위한 MVC 아키텍처를 제공하는 Spring의 모듈.
- **Spring Boot:** 높은 생산성을 제공하는 스타터 패키지와 자동 구성으로 Spring 기반 애플리케이션을 쉽게 개발하고 실행할 수 있게 도와주는 프로젝트.
---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 