---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 19일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "252"
tistoryPostUrl: https://yanacoding.tistory.com/252
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
<목차여기>
![](https://i.imgur.com/s735z9w.png)
# wrapper class
- 기본 자료형을 객체로 감싸는 역할
- 자료형에 대한 추가적인 기능을 제공하거나, 객체로서의 특징을 갖게 해줌
![](https://i.imgur.com/zMAqS56.png)
## wrapper class 사용 예시
```java
// 기본 자료형 사용
int primitiveInt = 10;

// Wrapper 클래스 사용 (Autoboxing: 기본 자료형을 Wrapper 클래스로 자동 변환)
Integer wrapperInt = 10;

// Autoboxing을 통해 기본 자료형을 Wrapper 클래스로 변환
// Unboxing을 통해 Wrapper 클래스를 기본 자료형으로 변환
int result = primitiveInt + wrapperInt;
```
```java
public class WrapperExample {
    public static void main(String[] args) {
        // Integer Wrapper 클래스 사용 예시
        Integer integerObj1 = new Integer(42); // 직접 생성
        Integer integerObj2 = 42; // Autoboxing: 기본 자료형을 Wrapper 클래스로 자동 변환

        // Autoboxing을 통해 기본 자료형을 Wrapper 클래스로 변환
        int intValue = integerObj1.intValue();

        // Double Wrapper 클래스 사용 예시
        Double doubleObj1 = new Double(3.14);
        Double doubleObj2 = 3.14;

        // 문자열을 정수로 변환하는 예시 (Wrapper 클래스 활용)
        String numberStr = "123";
        int convertedNumber = Integer.parseInt(numberStr);

        // Wrapper 클래스를 활용한 불리언 값 비교
        Boolean boolObj1 = true;
        Boolean boolObj2 = false;

        // Autoboxing을 통해 기본 자료형을 Wrapper 클래스로 변환
        boolean boolValue = boolObj1.booleanValue();
    }
}
```
# BigDecimal
- Java에서 정밀한 십진 연산을 수행하기 위한 클래스
- 부동 소수점 연산에서 발생할 수 있는 정확성 문제를 해결하기 위해 사용
- 즉, `BigDecimal`은 금융 계산이나 정확한 연산이 필요한 상황에서 사용
- 나눗셈의 경우 반드시 나누는 수를 지정하면서 나눗셈의 소수점 이하 자릿수와 반올림 모드를 지정해줘야함
```java
import java.math.BigDecimal;

public class BigDecimalExample {
    public static void main(String[] args) {
        // BigDecimal 객체 생성
        BigDecimal bigDecimal1 = new BigDecimal("123.45");
        BigDecimal bigDecimal2 = new BigDecimal("67.89");

        // 기본 산술 연산
        BigDecimal sum = bigDecimal1.add(bigDecimal2);
        BigDecimal difference = bigDecimal1.subtract(bigDecimal2);
        BigDecimal product = bigDecimal1.multiply(bigDecimal2);
        BigDecimal quotient = bigDecimal1.divide(bigDecimal2, 4, BigDecimal.ROUND_HALF_UP);

        // 출력
        System.out.println("Sum: " + sum);
        System.out.println("Difference: " + difference);
        System.out.println("Product: " + product);
        System.out.println("Quotient: " + quotient);
    }
}
```

# 연산자
[자바가 제공하는 다양한 연산자(산술연산자, 논리연산자, 비트연산자, 관계연산자, intanceof연산자, 비교연산자, 화살표연산자, 삼항연산자)와 연산자 우선순위](https://yanacoding.tistory.com/entry/Java-%EC%9E%90%EB%B0%94%EA%B0%80-%EC%A0%9C%EA%B3%B5%ED%95%98%EB%8A%94-%EB%8B%A4%EC%96%91%ED%95%9C-%EC%97%B0%EC%82%B0%EC%9E%90%EC%82%B0%EC%88%A0%EC%97%B0%EC%82%B0%EC%9E%90-%EB%85%BC%EB%A6%AC%EC%97%B0%EC%82%B0%EC%9E%90-%EB%B9%84%ED%8A%B8%EC%97%B0%EC%82%B0%EC%9E%90-%EA%B4%80%EA%B3%84%EC%97%B0%EC%82%B0%EC%9E%90-intanceof%EC%97%B0%EC%82%B0%EC%9E%90-%EB%B9%84%EA%B5%90%EC%97%B0%EC%82%B0%EC%9E%90-%ED%99%94%EC%82%B4%ED%91%9C%EC%97%B0%EC%82%B0%EC%9E%90-%EC%82%BC%ED%95%AD%EC%97%B0%EC%82%B0%EC%9E%90%EC%99%80-%EC%97%B0%EC%82%B0%EC%9E%90-%EC%9A%B0%EC%84%A0%EC%88%9C%EC%9C%84)
![](https://i.imgur.com/czFLXvq.png)
![](https://i.imgur.com/JGU0DIk.png)
![](https://i.imgur.com/5RFVHQk.png)

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 