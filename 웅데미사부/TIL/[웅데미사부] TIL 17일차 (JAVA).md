---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 17일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "250"
tistoryPostUrl: https://yanacoding.tistory.com/250
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗

# JDK, JRE, JVM
뭐지
![](https://i.imgur.com/IkrCAZH.png)
- JDK(Java Development Kit)
	- JRE를 포함, 자바로 개발이 가능한 환경 (JRE + Compilers + Debuggers)
- JRE(Java Runtime Environment)
	- 자바 소스코드를 실행할 수 있는 환경. (JVM + Libraries + other components)
- JVM(Java Virtual Machine)
	- JRE가 실행되고있는 플랫폼(OS)에 맞추어 java bytecode를 실행하는 가상 기계
	- JAVA가 OS 독립적으로 실행될 수 있도록 하기 위해 사용.
	- JVM이 OS독립적인것이 아닌 OS에 맞는 JVM을 제공하는 방식으로 OS 독립성 완성
관련해서 필요시 기존에 정리한 글 참조
- [JVM은 무엇이며 자바 코드는 어떻게 실행하는 것인가? (JVM, 컴파일 과정, 바이트 코드, JIT컴파일러, JDK, JRE)](https://yanacoding.tistory.com/entry/Java-JVM%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%9E%90%EB%B0%94-%EC%BD%94%EB%93%9C%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EA%B2%83%EC%9D%B8%EA%B0%80)
- [[JAVA] GC(Garbage collector, Garbage collection)](https://yanacoding.tistory.com/entry/JAVA-GCGarbage-collector-Garbage-collection)

# 조건문(Conditional Statements)
## if문
- 주어진 조건이 참인 경우에 코드블록 실행
```java
int number = 10;

if (number > 0) {
    System.out.println("양수입니다.");
} else if (number < 0) {
    System.out.println("음수입니다.");
} else {
    System.out.println("0입니다.");
}

```
## switch문
- 특정 변수의 값에 따라 여러가지 경우의 수 처리
```java
char grade = 'B';

switch (grade) {
    case 'A':
        System.out.println("우수");
        break;
    case 'B':
        System.out.println("보통");
        break;
    case 'C':
        System.out.println("미흡");
        break;
    default:
        System.out.println("평가 없음");
}
```
```java
// 동일하게 처리할 경우 아래처럼 사용 가능(A,B)
char grade = 'B';

switch (grade) {
    case 'A','B':
        System.out.println("보통");
        break;
    case 'C':
        System.out.println("미흡");
        break;
    default:
        System.out.println("평가 없음");
}
```
# 반복문
## for문
- 초기화, 조건 검사, 증감식이 각각 정의됨
```java
for (변수 초기화; 조건식; 증감식) {
    코드블록
}
for (int i = 1; i <= 5; i++) {
    System.out.println("현재 i의 값: " + i);
}
```
## while문
```java
while (조건문) {
	코드블록
}

int count = 0;

while (count < 3) {
    System.out.println("카운트: " + count);
    count++;
}
```
## do-while문
- 조건문이 참이건 아니건, 일단 1회는 실행 한 뒤 조건 판단
```java
int num = 1;

do {
    System.out.println("현재 숫자: " + num);
    num++;
} while (num <= 5);
```

# 메서드
- 특정한 작업을 수행하는 코드를 그룹화하고 이름을 붙여 호출할 수 있도록 함
```java
public class 클래스명 {
	//메서드 선언
    public 반환자료형 메서드명(자료형 매개변수명1, 자료형 매개변수명2,.) {
		코드블록
		return 반환자료형으로된반환값;
    }
    //메서드 사용
    메서드명(자료형 매개변수명1, 자료형 매개변수명2,.);
}
```
```java
//메서드 예시
public class Calculator {
    
    // 덧셈 메서드
    public int add(int a, int b) {
        return a + b;
    }

    // 곱셈 메서드
    public int multiply(int a, int b) {
        return a * b;
    }

    public static void main(String[] args) {
        Calculator calculator = new Calculator();

        // 덧셈 메서드 호출
        int sumResult = calculator.add(5, 3);
        System.out.println("덧셈 결과: " + sumResult);

        // 곱셈 메서드 호출
        int multiplyResult = calculator.multiply(4, 6);
        System.out.println("곱셈 결과: " + multiplyResult);
    }
}
```

# 메서드 오버로딩
- 같은 이름의 메서드를 여러 번 정의
- 메서드의 시그니처(메서드 이름, 매개변수의 타입 및 개수)가 다르면 동일한 이름의 메서드를 여러 개 선언할 수 있음
```java
public class Printer {

    // 정수 출력 메서드
    public void printNumber(int num) {
        System.out.println("숫자: " + num);
    }

    // 실수 출력 메서드
    public void printNumber(double num) {
        System.out.println("숫자: " + num);
    }

    public static void main(String[] args) {
        Printer printer = new Printer();

        // 정수 출력 메서드 호출
        printer.printNumber(10);

        // 실수 출력 메서드 호출
        printer.printNumber(3.14);
    }
}
```
* 참고 : [JAVA의 정성 객체지향 프로그래밍Ⅰ(2)- 오버로딩, 생성자, 변수의 초기화](https://yanacoding.tistory.com/entry/Java%EC%9D%98-%EC%A0%95%EC%84%9D-0604-0606-%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EC%8A%A4%EB%9E%98%EB%B0%8D%E2%85%A02-%EC%98%A4%EB%B2%84%EB%A1%9C%EB%94%A9-%EC%83%9D%EC%84%B1%EC%9E%90-%EB%B3%80%EC%88%98%EC%9D%98-%EC%B4%88%EA%B8%B0%ED%99%94)

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 


운용이 어렵다. 
장점을 얻어가기 어렵다.
서버대 서버간 통신이 함수호출보다 어렵기 때문이다. 번거롭고 이슈가 많이 생길 수 잇다
서버들 앞에 api 게이트웨이가 있고, api가 기능별로 쪼개어져 있다.
하나의 엔티티가 정해지면 엔티티별로 패키지를 구성하는 경우도, 기능별로 할수도.
한 엔티티마다 서비스가 나오는것.

node가 msa에 적합하다 서버대 서버가 통신할때 restapi로 연동하기 수월하다

멀티모듈
모노리포가 장점만 있는것도 아니고, 장점을 노리지 않는다.
중복코드를 제거할수있고 레이어를 나눌수있다.
번거로움이 좋은 경험치로 반환되기 어렵지 않을까 하는 우려가 있다.


rss로 해외 기업 블로그 구독하기도 함 정제되서 가끔씩 확인하는정도, 개발역량과 언어
spring data jpa를 사용하면서 복잡한 쿼리의 경우 다들 querydsl을 사용한다고 알고있는데요, 
저는 jpa를 최근들어 배우면서 querydsl의 오픈소스 라이브러리 마지막 업데이트가 2년전에 멈춰있어 jpa

크리텔 쿼리빌더 동적타이핑에대해서 불안해함 동적인 예외처리를 선호함

하둡에 기고

선택적으로 선택할수있다. 조직의 특수성이나 비즈니스의 특수성에따라 불호하는 팀원이 있을수있다.

성능이 떨어지지만 사람들이 선택한 근거는 분명하게 있다. 그렇다고 사용성이 좋아서 선택을 한거라고 보기에는 네티는 함수형과는 거리가 멀다.
---
형식  지필
시간 80분
범위 배운곳
객관식 주관식 - 주관식이 많음

