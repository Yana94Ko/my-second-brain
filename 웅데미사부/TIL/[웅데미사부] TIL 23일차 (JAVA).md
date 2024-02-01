---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 23일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "262"
tistoryPostUrl: https://yanacoding.tistory.com/262
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
## 자바 프로그래밍의 제네릭(generic) - JDK 1.5
자바에서 제네릭이란 데이터의 타입을 일반화 하는것을 의미함. 
클래스나 메소드에서 사용할 내부 데이터의 타입을 컴파일시에 미리 지정.

### 컴파일time type check 의 장점
- 클래스나 메소드 내부에서 사용되는 객체의 타입 안정성을 높일 수 있음.
- 반환값에 대한 타입 변환 및 타입검사에 들어가는 리소스를 줄일 수 있음.
	- JDK 1.5 이전에서는 여러 타입을 사용하는 대부분의 클래스나 메소드에서 인수나 반환값으로 Object 타입을 사용
	- 이 경우에는 반환된 Object 객체를 다시 원하는 타입으로 타입 변환해야 하며, 이때 오류가 발생할 가능성도 존재
### 제네릭의 선언 및 생성
```java
class MyArray<T> {
    T element;
    void setElement(T element) { this.element = element; }
    T getElement() { return element; }
}

MyArray<Integer> myArr = new MyArray<Integer>();
MyArray<Integer> myArr = new MyArray<>(); // Java SE 7부터 가능함.
```

### 제네릭 제거 시기
자바 코드에서 사용된 제네릭 타입은 컴파일시 컴파일러에 의해 자동으로 검사되어 타입 변환됨. 즉, 컴파일된 class 파일에는 어떠한 제네릭 타입도 남아있지 않음.

## 자바 프로그래밍의 함수형 프로그래밍 - JAVA 8
### 함수형 프로그래밍
자료 처리를 수학적 함수의 계산으로 취급하고 상태와 가변 데이터를 멀리하는 프로그래밍 패러다임의 하나.
명령형 프로그래밍에서는 상태를 바꾸는 것을 강조하는 것과는 달리, 함수형 프로그래밍은 함수의 응용을 강조한다. 프로그래밍이 문이 아닌 식이나 선언으로 수행되는 선언형 프로그래밍 패러다임을 따르고 있음. 함수형 프로그래밍은 1930년대에 계산가능성, 결정문제, 함수정의, 함수응용과 재귀를 연구하기 위해 개발된 형식체계인 람다 대수에 근간을 두고 있으며, 다수의 함수형 프로그래밍 언어들은 람다 연산을 발전시킨 것으로 볼 수 있음.
### 자바의 함수형 프로그래밍
자바는 Java 8 버전부터 함수형 프로그래밍을 지원하기 위해 람다(lambda)와 스트림(stream)이 도입됨. 람다와 스트림을 사용하면 함수형 프로그래밍 스타일로 자바 코드를 작성할 수 있음.

### 람다(Lambda)
익명 함수(anonymous function)를 의미. 인터페이스의 메서드가 1개 일 때 람다로 사용 할 수 있음(인터페이스의 메서드가 1개 이상이면 람다 함수를 사용할 수 없음 -> @FunctionalInterface 어노테이션 사용시 메서드를 2개이상 가진 인터페이스를 작성하는것이 불가하기 때문에 해당 어노테이션의 사용을 권장함)
#### 일반 코드
```java
interface Calculator {
    int sum(int a, int b);
}
class MyCalculator implements Calculator {
    public int sum(int a, int b) {
        return a+b;
    }
}
interface Calculator {
    int sum(int a, int b);
}

class MyCalculator implements Calculator {
    public int sum(int a, int b) {
        return a+b;
    }
}

public class Sample {
    public static void main(String[] args) {
        MyCalculator mc = new MyCalculator();
        int result = mc.sum(3, 4);
        System.out.println(result);  // 7 출력
    }
}
```
#### 람다를 적용한 코드
```java
@FunctionalInterface
interface Calculator {
    int sum(int a, int b);
}

public class Sample {
    public static void main(String[] args) {
        Calculator mc = (int a, int b) -> a +b;  // 람다를 적용한 코드
        int result = mc.sum(3, 4);
        System.out.println(result);
    }
}
```
참고 : Calculator 인터페이스의 메서드가 1개 이상이면 람다 함수를 사용할 수 없다.
### 람다 축약
#### 인터페이스에 이미 입출력에 대한 타입이 정의 -> 입력값의 자료형 생략
```java
interface Calculator {
    int sum(int a, int b);
}

public class Sample {
    public static void main(String[] args) {
        Calculator mc = (a, b) -> a +b;
        int result = mc.sum(3, 4);
        System.out.println(result);
    }
}
```
#### 어떤 클래스의 메서드를 사용하는 경우 -> `::`기호 활용 축약
```java
@FunctionalInterface
interface Calculator {
    int sum(int a, int b);
}

public class Sample {
    public static void main(String[] args) {
        Calculator mc = Integer::sum; //:: 활용 축약
        int result = mc.sum(3, 4);
        System.out.println(result);
    }
}
```

### 스트립(Stream)
글자 그대로 해석하면 ‘흐름, 개울’이라는 뜻. 데이터가 물결처럼 흘러가면서 필터링 과정을 통해 여러 번 변경되어 반환되기 때문에 이러한 이름을 가짐.
### 일반 코드
```java
import java.util.*;

public class Sample {
    public static void main(String[] args) {
        int[] data = {5, 6, 4, 2, 3, 1, 1, 2, 2, 4, 8};

        // 짝수만 포함하는 ArrayList 생성
        ArrayList<Integer> dataList = new ArrayList<>();
        for(int i=0; i<data.length; i++) {
            if(data[i] % 2 == 0) {
                dataList.add(data[i]);
            }
        }

        // Set을 사용하여 중복을 제거
        HashSet<Integer> dataSet = new HashSet<>(dataList);

        // Set을 다시 List로 변경
        ArrayList<Integer> distinctList = new ArrayList<>(dataSet);

        // 역순으로 정렬
        distinctList.sort(Comparator.reverseOrder());

        // Integer 리스트를 정수 배열로 변환
        int[] result = new int[distinctList.size()];
        for(int i=0; i< distinctList.size(); i++) {
            result[i] = distinctList.get(i);
        }
    }
}

```
### 스트림 코드
```java
import java.util.Arrays;
import java.util.Comparator;

public class Sample {
    public static void main(String[] args) {
        int[] data = {5, 6, 4, 2, 3, 1, 1, 2, 2, 4, 8};
        int[] result = Arrays.stream(data)  // IntStream을 생성한다.
                .boxed()  // IntStream을 Stream<Integer>로 변경한다.
                .filter((a) -> a % 2 == 0)  //  짝수만 뽑아낸다.
                .distinct()  // 중복을 제거한다.
                .sorted(Comparator.reverseOrder())  // 역순으로 정렬한다.
                .mapToInt(Integer::intValue)  // Stream<Integer>를 IntStream으로 변경한다.
                .toArray()  // int[] 배열로 반환한다.
                ;
    }
}

```
### [JAVA의 Stream API](https://yanacoding.tistory.com/entry/JAVA-Stream-API)

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 