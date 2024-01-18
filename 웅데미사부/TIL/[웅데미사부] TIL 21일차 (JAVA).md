---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 21일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "254"
tistoryPostUrl: https://yanacoding.tistory.com/254
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗

# Array
## 배열이란?
Java의 배열은 고정 크기의 데이터 구조로, 동일한 데이터 형식의 요소를 담을 수 있음.
배열의 크기는 생성 시에 지정되며, 한 번 생성된 배열의 크기는 변경할 수 없음
## 배열의 생성과 초기화, 요소로의 접근
```java
// 정수형 배열 생성과 초기화
int[] intArray = {1, 2, 3, 4, 5};

// 문자열 배열 생성과 초기화
String[] stringArray = {"apple", "banana", "orange"};

// 배열 요소에 접근
int firstElement = intArray[0];
String fruit = stringArray[1];
```
## 대표적인 메서드
### length
- 배열 길이 반환
```java
int length = intArray.length; // 결과: 5
```
### clone()
- 배열 복제
```java
int[] clonedArray = intArray.clone();
```
### equals(Object array)
- 두 배열이 동일한지 확인
```java
boolean isEqual = Arrays.equals(intArray, clonedArray);
```
### sort(int[] array)
- 배열 오름차순 정렬
```java
Arrays.sort(intArray);
```
### toString()
- 배열의 내용을 문자로 반환
```java
String arrayString = Arrays.toString(intArray);
```
### compare(arrays1, array2)
- 배열의 각 요소를 순차적으로 비교하면서, 첫 번째로 다른 요소를 찾아 그 크기를 반환
- 두 배열이 동일하다면 `0`을 반환
```java
import java.util.Arrays;

public class ArraysCompareExample {
    public static void main(String[] args) {
        // 두 배열 비교
        int[] array1 = {1, 2, 3};
        int[] array2 = {1, 2, 3};
        int[] array3 = {1, 2, 4};

        int result1 = Arrays.compare(array1, array2); // 결과: 0 (동일)
        int result2 = Arrays.compare(array1, array3); // 결과: -1 (array1이 작음)

        System.out.println("Compare Result 1: " + result1);
        System.out.println("Compare Result 2: " + result2);
    }
}
```
### fill(array, element)
- 배열의 모든 요소를 지정된 값으로 채움
```java
import java.util.Arrays;

public class ArraysFillExample {
    public static void main(String[] args) {
        // 배열 초기화
        int[] numbers = new int[5];

        // 배열을 7로 채우기
        Arrays.fill(numbers, 7);

        // 결과 출력[7, 7, 7, 7, 7]
        System.out.println("Filled Array: " + Arrays.toString(numbers));
    }
}
```
# Array List
## 배열 기반의 리스트란?
java는 크기가 동적으로 조절 가능한 배열 기반의 리스트를 제공
기본 자료형을 저장할 수 없으며, 객체를 저장함.
유연하게 크기를 조절할 수 있어 데이터를 동적으로 관리하는 데 효과적임
## ArrayList의 생성과 요소 추가 및 접근
```java
// 문자열을 저장하는 ArrayList 생성
ArrayList<String> stringList = new ArrayList<>();

// 요소 추가
stringList.add("apple");
stringList.add("banana");
stringList.add("orange");

// 요소 접근
String firstElement = stringList.get(0);
```
## 대표 메서드
### add(E element)
- 요소를 리스트에 추가
```java
stringList.add("grape");
```
### get(int index)
- 지정된 인덱스에 있는 요소 반환
```java
String fruit = stringList.get(1); // 결과: "banana"
```
### remove(int index)
- 지정된 인덱스에 있는 요소 삭제
```java
stringList.remove(2);
```
### size()
- 리스트 크기 반환
```java
int size = stringList.size(); // 결과: 3
```
### contains(Object element)
- 해당 요소가 리스트에 포함되어있는지 확인
```java
boolean containsBanana = stringList.contains("banana");
```
### toArray()
- 리스트를 배열로 반환
```java
String[] arrayFromList = stringList.toArray(new String[0]);\
```

# Date
java에서 날짜와 시간 정보를 표현하는 클래스이나, java 8부터는 deprecated(사용을 권장하지 않음)
현재는 `java.time` 패키지에서 `LocalDate`, `LocalTime`, `LocalDateTime` 등을 사용하는 것이 권장

# LocalDate, LocalTime, LocatDateTime
기존의 `Date` 클래스보다 훨씬 강력하고 사용하기 편리하며, 시간대(TimeZone)와 무관하게 지역(local) 날짜와 시간을 다룰 수 있음
## LocalDate 클래스
- 날짜 정보를 나타내는 클래스로, 연, 월, 일 정보를 가짐
- 불변(Immutable)하며, 시간대 정보가 없음.
## LocalTime 클래스
- 시간 정보를 나타내는 클래스로, 시, 분, 초, 나노초 정보를 가짐
- 불변(Immutable)하며, 날짜 정보가 없음
## LocatDateTime 클래스
- 날짜와 시간 정보를 모두 가지고 있는 클래스로, 연, 월, 일, 시, 분, 초, 나노초 정보를 가짐
- 불변(Immutable)하며, 시간대 정보가 없음
## 대표적인 메서드
### now()
- 현재 날짜 및 시간을 반환
```java
LocalDate currentDate = LocalDate.now();
LocalTime currentTime = LocalTime.now();
LocalDateTime currentDateTime = LocalDateTime.now();
```
### of(int year, int month, int dayOfMonth)
- 주어진 연, 월, 일로 `LocalDate` 객체를 생성
```java
LocalDate customDate = LocalDate.of(2022, 1, 14);
```
### of(int hour, int minute, int second)
- 주어진 시, 분, 초로 `LocalTime` 객체를 생성
```java
LocalTime customTime = LocalTime.of(12, 30, 45);
```
### of(int year, int month, int dayOfMonth, int hour, int minute, int second)
- 주어진 연, 월, 일, 시, 분, 초로 `LocalDateTime` 객체를 생성
```java
LocalDateTime customDateTime = LocalDateTime.of(2022, 1, 14, 12, 30, 45);
```
### isBefore() / isAfter()
- 날짜와 시간을 비교하여 순서를 확인
```java
boolean isBefore = currentDateTime.isBefore(customDateTime);
boolean isAfter = currentDateTime.isAfter(customDateTime);
```
## DateTimeFormatter
날짜 및 시간을 원하는 형식으로 변환하는 데 사용되는 클래스
```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

public class LocalDateFormattingExample {
    public static void main(String[] args) {
        // 현재 날짜
        LocalDate currentDate = LocalDate.now();

        // 기본 형식 (ISO_LOCAL_DATE)
        String formattedDate1 = currentDate.format(DateTimeFormatter.ISO_LOCAL_DATE);
        System.out.println("Default Format: " + formattedDate1);

        // 사용자 정의 형식
        DateTimeFormatter customFormatter = DateTimeFormatter.ofPattern("yyyy/MM/dd");
        String formattedDate2 = currentDate.format(customFormatter);
        System.out.println("Custom Format: " + formattedDate2);
    }
}
```


---
# 오늘의 멘토링 🥸
- Q1 : Mongo DB 스티디를 진행한다고 하면, 어떤 부분에 주안점을 두고 스터디를 진행하는게 좋을까요? (이번 교육 내부가 아닌, 외부 커뮤니티에서 현업자들이 때마침 mongoDB 스터디를 진행 한다고 해서 참여할 예정입니다..!)
	- A : 실습이 병행된 스터디를 추천한다. 레플리카 샤딩을 구성해서 기존에 사용하던 DB와의 차이를 체감하는 스터디를 진행해봤으면 한다. mysql의 도큐먼트 디비 특성을 살려 도큐먼트 단위 트랜젝션을 실습하면서, 기존에 자주 사용하던 mysql과 다른게 뭔지 파고드는게 좋다. 도서보다는 mongodb를 사용하는 해외 기업들의 아티클과 국내 기업들의 아티클을 읽어보는것을 추천한다.

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 