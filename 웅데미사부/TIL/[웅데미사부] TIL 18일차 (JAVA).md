---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 18일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "251"
tistoryPostUrl: https://yanacoding.tistory.com/251
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
<목차여기>

# 자바에서의 객체지향형 프로그래밍과 함수형 프로그래밍
오늘 강의에서는 자바의 캡슐화와 객체지향 프로그래밍, 함수형 프로그래밍에 대해서 다루었다. 
그 중 자바의 객체지향 프로그래밍과, 캡슐화에 대해서 기존에 정리한 글을 첨부한다.
[자바의 패키지(package), import, 클래스패스(CLASSPATH,-d,-cp), 접근 제어자(private, public, defalt, protected), 캡슐화(데이터하이딩, 객체지향, 겟터getter,셋터setter)](https://yanacoding.tistory.com/entry/Java-%EC%9E%90%EB%B0%94%EC%9D%98-%ED%8C%A8%ED%82%A4%EC%A7%80package)

자바의 함수형 프로그래밍에 대해서는, 사실 여태 한번도 사용해본 바가 없어 이번 기회에 코드를 통해 한번 비교해보고자 한다.

## 자바 객체지향 코드(OOP) 예시
```java
// Calculator
package programming.oop;

public interface  {
    void add(int x);

    void minus(int x);

    void multiply(int x);

    void divide(int x);
}
// OOPCalculator
package programming.oop;

import lombok.ToString;

@ToString
public class OOPCalculator implements Calculator {

    private Integer result;

    public OOPCalculator() {
        this.result = 0;
    }

    @Override
    public void add(int x) {
        this.result += x;
    }

    @Override
    public void minus(int x) {
        this.result -= x;
    }

    @Override
    public void multiply(int x) {
        this.result *= x;
    }

    @Override
    public void divide(int x) {
        if (x != 0) this.result /= x;
    }

    public Integer result() {
        return result;
    }
}
// OOPCalculatorApp
package programming.oop;

public class OOPCalculatorApp {
    public static void main(String[] args) {
        OOPCalculator calculator = new OOPCalculator();

        calculator.add(3);
        calculator.minus(1);
        calculator.multiply(5);
        calculator.divide(2);

        System.out.println(calculator.result());
    }
}
```
## 자바 함수형 프로그래밍(FP) 예시
```java
//FunctionalCalculator
package programming.fp;

import java.util.function.BiFunction;

public class FunctionalCalculator {

    static BiFunction<Integer, Integer, Integer> add =
            (x, y) -> x + y;
    static BiFunction<Integer, Integer, Integer> minus =
            (x, y) -> x - y;
    static BiFunction<Integer, Integer, Integer> multiply =
            (x, y) -> x * y;
    static BiFunction<Integer, Integer, Integer> divide =
            (x, y) -> (y != 0) ? x / y : 0;
}
//FunctionalCalculatorApp
package programming.fp;

import java.util.function.BiFunction;

import static programming.fp.FunctionalCalculator.*;

public class  {
    public static void main(String[] args) {
        int x = 0;

        x = add.apply(x, 3);
        x = minus.apply(x, 1);
        x = multiply.apply(x, 5);
        x = divide.apply(x, 2);

        System.out.println(x);
    }
}

```

## 두 예시코드 비교
1. **가독성:**
    - 객체지향 프로그래밍은 메소드와 멤버 변수를 사용하여 객체의 상태와 행동을 모델링하므로 일반적으로 가독성이 좋음
    - 함수형 프로그래밍은 람다 표현식을 사용하고 함수를 일급 시민으로 취급하므로 간결하지만 초보자에게는 어려울 수 있음
2. **상태 변이:**
    - 객체지향 프로그래밍은 객체의 상태를 변이시키는 메소드를 호출하여 작동하므로 상태 변이가 자연스러움
    - 함수형 프로그래밍은 불변성을 강조하며 함수는 입력을 받아 출력을 생성하므로 상태 변이가 적음
3. **확장성:**
    - 객체지향 프로그래밍은 새로운 클래스와 상속을 통해 확장
    - 함수형 프로그래밍은 함수를 조합하고 고차 함수를 사용하여 확장
4. **부수 효과:**
    - 객체지향 프로그래밍은 상태 변이와 부수 효과가 자연스러움
    - 함수형 프로그래밍은 부수 효과를 피하려고 노력하며 불변성을 강조

# 객체지향 설계의 다섯 가지 원칙(SOLID)
## 단일 책임 원칙(Single Responsibility Principle, SRP)
- 한 클래스는 하나의 책임만 가져야 함
```java
// 잘못된 예시
class Employee {
    void calculateSalary() {
        // 급여 계산 로직
    }

    void generateReport() {
        // 보고서 생성 로직
    }
}

// 올바른 예시
class Employee {
    void calculateSalary() {
        // 급여 계산 로직
    }
}

class ReportGenerator {
    void generateReport() {
        // 보고서 생성 로직
    }
}

```
## 개방-폐쇄 원칙(Open/Closed Principle, OCP)
- 소프트웨어 엔티티(클래스, 모듈, 함수 등)는 확장에 대해 열려 있어야 하고, 수정에 대해서는 닫혀 있어야함
```java
// 잘못된 예시
class Rectangle {
    int width;
    int height;
}

class AreaCalculator {
    double calculateArea(Rectangle rectangle) {
        return rectangle.width * rectangle.height;
    }
}

// 올바른 예시
interface Shape {
    double calculateArea();
}

class Rectangle implements Shape {
    int width;
    int height;

    @Override
    public double calculateArea() {
        return width * height;
    }
}

class Circle implements Shape {
    int radius;

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

```
## 리스코프 치환 원칙(Liskov Substitution Principle, LSP)
- 하위 타입은 언제나 상위 타입으로 교체할 수 있어야 함
```java
// 잘못된 예시
class Bird {
    void fly() {
        // 날기 로직
    }
}

class Penguin extends Bird {
    void fly() {
        throw new UnsupportedOperationException("Penguins can't fly");
    }
}

// 올바른 예시
interface Flyable {
    void fly();
}

class Bird implements Flyable {
    @Override
    public void fly() {
        // 날기 로직
    }
}

class Penguin implements Flyable {
    @Override
    public void fly() {
        throw new UnsupportedOperationException("Penguins can't fly");
    }
}

```
## 인터페이스 분리 원칙(Interface Segregation Principle, ISP)
- 클라이언트는 자신이 사용하지 않는 인터페이스에 의존하면 안됨
```java
// 잘못된 예시
interface Worker {
    void work();
    void eat();
}

class Engineer implements Worker {
    @Override
    public void work() {
        // 엔지니어의 작업 로직
    }

    @Override
    public void eat() {
        // 엔지니어의 식사 로직
    }
}

// 올바른 예시
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

class Engineer implements Workable, Eatable {
    @Override
    public void work() {
        // 엔지니어의 작업 로직
    }

    @Override
    public void eat() {
        // 엔지니어의 식사 로직
    }
}
```
## 의존 역전 원칙(Dependency Inversion Principle, DIP)
- 고수준 모듈은 저수준 모듈에 의존하면 안 되며, 둘 모두 추상화에 의존해야함
```java
// 잘못된 예시
class LightBulb {
    void turnOn() {
        // 전구를 켜는 로직
    }

    void turnOff() {
        // 전구를 끄는 로직
    }
}

class Switch {
    LightBulb bulb = new LightBulb();

    void operate() {
        if (bulb.isOn()) {
            bulb.turnOff();
        } else {
            bulb.turnOn();
        }
    }
}

// 올바른 예시
interface Switchable {
    void turnOn();
    void turnOff();
}

class LightBulb implements Switchable {
    @Override
    public void turnOn() {
        // 전구를 켜는 로직
    }

    @Override
    public void turnOff() {
        // 전구를 끄는 로직
    }
}

class Switch {
    Switchable device;

    void operate() {
        if (device.isOn()) {
            device.turnOff();
        } else {
            device.turnOn();
        }
    }
}
```
---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 