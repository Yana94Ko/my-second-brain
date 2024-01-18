---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 20일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "253"
tistoryPostUrl: https://yanacoding.tistory.com/253
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗

# String
- 자바에서 String은 참조형 타입
- 참조형이므로 실제 데이터가 아닌 메모리 내에서의 주소를 저장하며, 불변(immutable)성을 가지고 있음
- 즉, 한 번 생성된 문자열은 변경할 수 없음을 의미하며, 새로운 문자열이 필요할 때마다 새로운 객체를 생성
## concat(String str)
- 현재 문자열에 인자로 전달된 문자열을 덧붙여 새로운 문자열을 반환
```java
String str1 = "Hello";
String str2 = " World";
String result = str1.concat(str2);
// 결과: "Hello World"

```
## replace(CharSequence target, CharSequence replacement)
- 지정된 문자열 또는 문자 시퀀스를 새로운 문자열로 대체
```java
String original = "apple";
String replaced = original.replace("p", "P");
// 결과: "aPple"
```
## join(CharSequence delimiter, CharSequence... elements)
- 문자열 배열을 지정된 구분자(delimiter)로 결합
```java
String[] words = {"Java", "is", "fun"};
String joined = String.join(" ", words);
// 결과: "Java is fun"
```
## contains(CharSequence sequence)
- 주어진 문자열이 현재 문자열에 포함되어 있는지 여부를 확인
```java
String str = "Java Programming";
boolean containsJava = str.contains("Java");
// 결과: true
```
## equals(Object another)
- 주어진 객체 또는 문자열과 현재 문자열을 비교
```java
String str1 = "Java";
String str2 = "java";
boolean isEqual = str1.equals(str2);
// 결과: false
```
## equalsIgnoreCase(String another)
- 주어진 객체 또는 문자열과 현재 문자열을 비교(대소문자를 무시)
```java
String str1 = "Java";
String str2 = "java";
boolean isEqual = str1.equalsIgnoreCase(str2);
// 결과: true
```
## split(String regex)
- 주어진 정규 표현식을 기준으로 문자열을 분할하고, 문자열 배열로 반환합니다.
```java
String sentence = "Java is fun!";
String[] words = sentence.split(" ");
// 결과: ["Java", "is", "fun!"]
```
## trim()
- 문자열의 앞뒤에 있는 공백을 제거
```java
String str = "   Hello, World!   ";
String trimmedStr = str.trim();
// 결과: "Hello, World!"
```

# String, String Buffer, String Builder
## String
- 불변(Immutable)
- 따라서, 문자열 수정 시 새로운 객체를 생성하므로 메모리 사용이 더 많음
## String Buffer
- 가변(Mutable)
- 문자열을 수정할 때 사용
- 스레드에 안전한 동기화된 메소드를 제공
## String Builder
- 가변(Mutable)
- 문자열을 수정할 때 사용
- 동기화를 지원하지 않음(단일 스레드 환경에서 성능이 더 우수)
## toString()
- String Buffer, String Builder를 String으로 반환
```java
StringBuilder builder = new StringBuilder("Hello");
builder.append(", ").append("World");
String result1 = builder.toString();
StringBuffer buffer = new StringBuffer("Hello");
buffer.append(", ").append("World");
String result2 = buffer.toString();

```
## 비교 및 선택 가이드:
- **단일 스레드 환경:** `StringBuilder`를 사용하여 성능을 최적화
- **멀티스레드 환경:** `StringBuffer`를 사용하여 스레드 안정성을 보장
- **불변성이 필요한 경우:** `String`을 사용하여 안정성을 확보

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 