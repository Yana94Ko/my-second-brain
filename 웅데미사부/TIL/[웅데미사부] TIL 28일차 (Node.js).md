---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 28일차 (Node.js)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "277"
tistoryPostUrl: https://yanacoding.tistory.com/277
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗

## JDBC, Hibernate, JPA, Spring Data JPA 
## JDBC (Java Database Connectivity)

- **개요:**
    - 자바 애플리케이션과 데이터베이스 간의 연결을 제공하는 자바 API.
    - SQL 쿼리를 실행하고 관계형 데이터베이스와 상호 작용할 수 있는 방법을 제공한다.
- **특징:**
    - **수동적인 데이터베이스 처리:** SQL 쿼리를 직접 작성하고 처리해야 한다.
    - **직접적인 커넥션 관리:** Connection, Statement, ResultSet 등을 명시적으로 열고 닫아야 한다.
    - **좋은 성능:** 직접적인 접근으로 인해 일부 상황에서 더 나은 성능을 제공할 수 있다.

## Hibernate
- **개요:**
    - 객체 관계 매핑 (ORM)을 위한 프레임워크로, 자바 객체와 데이터베이스 테이블 간의 매핑을 자동화한다.
    - JDBC의 복잡성을 줄이고 객체 지향 프로그래밍을 편리하게 할 수 있도록 도와준다.
- **특징:**
    - **ORM 기능 제공:** 자바 객체와 데이터베이스 테이블 간의 매핑을 어노테이션 또는 XML 설정을 통해 정의하고 제공한다.
    - **캐시 기능:** 성능 향상을 위해 데이터베이스 결과를 캐싱할 수 있다.
    - **높은 생산성:** 데이터베이스와 상호 작용하는 코드를 최소화하고 객체 중심의 코드 작성을 가능하게 한다.

## JPA (Java Persistence API
- **개요:**
    - 자바에서 객체 관계 매핑을 위한 표준 인터페이스.
    - Hibernate, EclipseLink 등의 구현체가 JPA 표준을 따르고 있으며, 개발자는 특정 구현체에 종속되지 않고 JPA 인터페이스를 사용할 수 있다.
- **특징:**
    - **표준 인터페이스:** JPA는 인터페이스를 정의하고, 구현체는 이 인터페이스를 구현하여 객체와 데이터베이스 간의 매핑을 지원한다.
    - **객체 지향적인 쿼리 언어:** JPQL (Java Persistence Query Language)을 사용하여 객체 지향적인 방식으로 데이터베이스 쿼리를 작성할 수 있다.
    - **트랜잭션 관리:** JPA는 트랜잭션을 관리하며, 객체의 변경 사항을 트랜잭션 단위로 처리한다.

## Spring Data JPA
- **개요:**
    - 스프링에서 JPA를 쉽게 사용할 수 있도록 도와주는 프로젝트.
    - JPA의 기능을 더 쉽게 사용하고 빠르게 개발할 수 있도록 스프링 기반의 기능을 제공한다.
- **특징:**
    - **Repository 인터페이스:** 데이터베이스 조작을 위한 공통 메서드를 제공하는 Repository 인터페이스를 사용하여 데이터베이스와 손쉽게 상호 작용할 수 있다.
    - **쿼리 메서드:** 메서드 이름에 따라 자동으로 쿼리를 생성해주는 쿼리 메서드를 지원한다.
    - **동적 쿼리 생성:** 조건에 따라 동적으로 쿼리를 생성할 수 있는 기능을 제공한다.

## 결론
- **JDBC:** 수동적이고 직접적인 데이터베이스 처리를 위한 자바 API.
- **Hibernate:** ORM 프레임워크로, 객체와 데이터베이스 간의 매핑을 자동화해주는 기능을 제공한다.
- **JPA:** 자바에서 ORM을 위한 표준 인터페이스로, 구현체에 독립적으로 사용할 수 있다.
- **Spring Data JPA:** 스프링에서 JPA를 더 편리하게 사용하기 위한 프로젝트로, Repository 인터페이스와 다양한 기능을 제공한다.
## [Rest API](https://yanacoding.tistory.com/entry/CS-WEB-HTTP-RESTful-API%EB%9E%80API-REST-API-RESTful-API)
## Node.js 와 Express js 그리고 NestJS
## JavaScript (JS)
- **개요:**
  - 웹 브라우저에서 실행되는 스크립트 언어로, 주로 클라이언트 측 웹 개발에서 사용된다.
  - 객체 지향 프로그래밍 언어이며, 동적 타입 언어로 변수의 타입을 런타임에 결정한다.

## V8 JavaScript Engine
- **개요:**
  - Google에서 개발한 오픈 소스 JavaScript 엔진.
  - 주로 웹 브라우저 (Google Chrome)과 Node.js에서 사용되며, 빠른 성능과 최적화된 메모리 관리를 제공한다.

## Node.js
- **개요:**
  - Chrome V8 엔진을 기반으로 하는 JavaScript 런타임 환경.
  - 서버 측 JavaScript 실행을 가능하게 하며, 비동기적이고 이벤트 기반의 I/O를 지원한다.
  - npm (Node Package Manager)을 통해 패키지 관리가 가능하다.

## Express.js
- **개요:**
  - Node.js를 위한 웹 애플리케이션 프레임워크.
  - 빠르고 간편한 라우팅 및 미들웨어 지원으로 웹 애플리케이션 개발을 용이하게 한다.
  - MVC 아키텍처를 따르며, RESTful API를 쉽게 구축할 수 있다.

## NestJS
- **개요:**
  - TypeScript를 기반으로 하는 서버 사이드 웹 프레임워크.
  - Angular 개발자들이 친숙한 구조와 패턴을 사용하여 백엔드를 개발할 수 있도록 해준다.
  - Express를 기반으로 한다.

## 결론
- **JavaScript (JS):** 웹 브라우저에서 사용되는 스크립트 언어.
- **V8 JavaScript Engine:** Google에서 개발한 JavaScript 엔진으로, 빠른 성능과 최적화된 메모리 관리를 제공한다.
- **Node.js:** Chrome V8 엔진을 기반으로 하는 JavaScript 런타임 환경으로, 서버 측 JavaScript 실행을 가능하게 한다.
- **Express.js:** Node.js를 위한 웹 애플리케이션 프레임워크로, 간편한 라우팅 및 미들웨어 지원을 제공한다.
- **NestJS:** TypeScript를 기반으로 하는 서버 사이드 웹 프레임워크로, Angular 스타일의 구조와 패턴을 사용하여 개발자에게 편의성을 제공한다.

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 