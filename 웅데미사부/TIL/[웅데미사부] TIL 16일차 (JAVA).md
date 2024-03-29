---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 16일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "247"
tistoryPostUrl: https://yanacoding.tistory.com/247
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗

# JShell :  JAVA REPL(Read Eval Print Roop)
- 파이썬의 Python shell처럼, 한줄씩 코드를 실행시켜준다.
## JSell 설치방법
- java 9 버전 이상 : java 설치시 기본 제공
- java 9 이전 버전에서 사용하기 원할 시 : [Stack overflow 참고](https://stackoverflow.com/questions/53475519/id-like-to-use-jshell-with-jdk-8)
## JShell 사용법
- JAVA가 설치된 터미널 혹은 CLI에서 "jshell" 입력시 jshell 사용모드 진입
```cmd
➜  ~ jshell
|  Welcome to JShell -- Version 19.0.2
|  For an introduction type: /help intro

jshell> System.out.println("Hello world");
Hello world

jshell>
```
## JShell 종료법
- /exit
```cmd
jshell> /exit
|  Goodbye
➜  ~
```

---

# 구구단 표 나누기 과제
## 구구단 표 Multiplication Table
## 정수([Integer](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html))

![](https://i.imgur.com/UndsWfk.png)

## 연산자
# Console에 출력값 띄우기
## System.out.print("출력할 문자열");
## System.out.println("출력 후 개행할 문자열");
## System.out.printf("출력 서식", 출력내용1, 출력내용2.,);
- /n
### 출력 서식
- `%[-][0][n][.m]` + `지시자`
#### -
- (생략 가능) 전체 자리수가 지정된 경우 왼쪽 정렬하고 빈칸에 공백 출력
#### 0
- (생략 가능) 전체 자리수가 지정된 경우 오니쪽의 남는 자리에 0을 출력
#### n
- (생략 가능) 출력할 전체 자릿수 지정
#### .m
- (생략 가능) 소수점 아래 자리수 지정. 잘리는 소수점 자리수는 반올림.
#### 지시자
| **지시자** | **설명** |
| ---- | ---- |
| %b | **boolean** 형식으로 출력 |
| %d | 정수 형식으로 출력 |
| %o | 8진수 정수의 형식으로 출력 |
| %x 또는 %X | 16진수 정수의 형식으로 출력 |
| %f | 소수점 형식으로 출력 |
| %c | 문자형식으로 출력 |
| %s | 문자열 형식으로 출력 |
| %n | 줄바꿈 기능 |
| %e 또는 %E | 지수 표현식의 형식으로 출력 |
| %t | date, time 형식으로 출력 |
#### 사용 예시
```java
// 정수
System.out.printf("%d", 85);   //85(10진수로 출력)
System.out.printf("%7d", 85);  //     85(7자리, 빈자리는 공백으로 처리)
System.out.printf("%-7d", 85); //85     (7자리, 빈자리는 공백으로 처리, 왼쪽정렬)
System.out.printf("%07d", 85); //0000085(7자리, 빈자리는 0으로 채움)

// 문자열
System.out.printf("%s", "hello"); 	//hello(문자열로 출력)
System.out.printf("%7s", "hello");	//  hello(7자리, 빈자리는 공백으로 처리)
System.out.printf("%-7s", "hello");	//hello  (7자리, 빈자리는 공백으로 처리, 왼쪽정렬)

// 실수
System.out.printf("%f", 3.14);		//3.140000(10진수 실수, 소수점 이하 자릿수의 default는 6자리)
System.out.printf("%5.1f", 3.14);	//  3.1(소수점 이하 포함 5자리, 소수점 이하 1자리) 
System.out.printf("%05.1f", 3.14);	//003.1(소수점 이하 포함 5자리, 소수점 이하 1자리, 빈자리 0)
System.out.printf("%-5.1f", 3.14);	//3.1  (소수점 이하 포함 5자리, 소수점 이하 1자리, 왼쪽정렬)
```
![](https://i.imgur.com/uhVg6Yq.png)

## 사실 이렇게 열심히 배운 System.out.print~는,  현업에서는 사용을 지양해야 한다.
- 관련 이슈는 [[[JAVA] System.out.print~의 사용을 지양해야만 하는 이유를 알아보자(feat,, IO, 휘발성, 출력레벨, 성능저하..)]]에서 추가적으로 알아보도록 하자.
# 리터럴
- '값 그 자체'를 의미
- cf) 변수 : 하나의 값을 저장하기 위한 공간, 상수 : 값을 한번만 저장 할 수 있는 공간.
# 연산자
## 산술 연산자
### `+`연산자 : 덧셈
```java
jshell> 5 + 2;
$1 ==> 7
```
### `-`연산자 : 뺄셈
```java
jshell> 5 - 2;
$2 ==> 3
```
### `*`연산자 : 곱셈
```java
jshell> 5 * 2;
$3 ==> 10
```
### `/`연산자 : 나눗셈(정수 - 몫 반환)
```java
jshell> 5 / 2;
$4 ==> 2
```
### `%`연산자 : 나눗셈(나머지 반환)
- mod, modulo, 모듈로라고도 함.
- 정수와 부동소수점수 연산 모두에 사용 할 수 있음.
```java
jshell> 5 % 2;
$5 ==> 1
```
## 대입연산자

# 변수
- 단 하나의 값을 저장 할 수 있는 메모리 공간
## 변수의 초기화
- 변수를 사용하기 전, 처음으로 값을 저장한다고 선언하는 것
- 메모리에 garbage vlaue가 남아있을 수 있기 때문에, 변수를 초기화하는것이 좋음.
## 자바의 변수 네이밍 규칙
1. 첫 글자는 문자( 대/소문자 ), 밑줄( _ ), 달러기호( $ )로 시작해야함.
2. 문자( 대/소문자 ), 밑줄( _ ), 달러기호( $ ), 숫자 사용 가능
3. 예약어 사용 금지
	- int, class, static, String,,.
4. 대소문자를 구분함
5. (관례) 카멜 케이스를 사용함
## 자바 기본 자료형
![[JAVA/mindmap/자료형|자료형]]


---
# 오늘의 멘토링 🥸
- Q1 : oSQL에서 no의 해석에서는 의견이 갈린다고 들었습니다. 멘토님께서는 NoSQL에서 no를 어떻게 해석하시나요?  
		- no
		- not only
		- non-relational operational
		- non-relational database
	- A : no는 not only. sql이 DB에서 우선순위가 높은 선택지였을때 나온것이 noSQL이라 불리우는 범주의 DB였기 때문. 즉, RDB만으로는 해결하기 어려운 문제가 점차 가속되던 상태에서 나온것이 noSQL(데이터가 늘어나는데 RDB에서는 그를 따라갈만한 퍼포먼스가 잘 나오지 않았고, DB가 못견뎌서 램을 도배하던가 등등의 방식으로 나오고있었음)
- Q2 : 한국에서는 not-only로 해석하는 경우가 주류라고 들었는데, 만약 not-only로 해석한다면, SQL은 NoSQL의 하위집합인걸까요..?
	- A : nosql은 db하면 sql을 사용하던 시기에 사용하던 명칭이며, 실제론 하나의 DB종류라고 보기에는 어려운 다양한 종류의 DB를 포괄적으로 지칭하는 용어임.
- Q3 : 더불어서 멘토님께서는 현업에서 어떤 형태의 DB를 사용하시는지, 보통 어떠한 때에 NoSQL을 사용하시고, 어떠한 때에 RDBMS를 사용하시는지 궁금합니다..!
	- A : document 단위 트랜잭션을 지원하기때문에 noSQL을 선호하는 편이며, RDBMS를 선호하지 않음. 하지만 협업을 하기위해서는 여러 팀원들의 불안감을 모두 설득하는 것이 어려워 RDB를 주로 사용함. 하지만 RDB의 트랜잭션은 정합성을 담보로 성능을 내어주는 선택이라 생각하기 때문에, 혼자 진행하는 프로젝트라면 no sql을 주로 사용함.
- Q4 : Q. 현업에서는 개발을 하실 때 어느정도까지 log를 남기시나요?
	Java 강의 수강 도중 console에 출력하는 System.out에 대해서 다루었습니다. sout 관련해서 기존부터 받아왔던 “Sout은 성능면에서나 로그를 남기는 이유와 관련해서나, Sout 사용을 지양하고 logger또는 logger 프레임워크를 사용하는것이 좋습니다” 라는 피드백이 생각나,  **“왜 개발 및 운영환경에서 Sout의 사용을 지양해야하는지”** 이번 기회에 공부해보았습니다…
	관련해서 생긴 궁금증으로는 **“운영환경이 아닌 개발환경에서 임시로 디버깅을 하기 위해서는 System.out을 사용해도 괜찮지 않을까?“라는 생각이 듭니다.** 하지만 이러한 궁금증 관련해서 전자정부 프레임워크의 메뉴얼에서도 “개발/테스팅 시점에만 System.out.println()을 사용하고 운영으로 이관하기 전에 삭제하는 것은 좋은 방법이 아님.“라고 하는데, 그 이유가 궁금합니다..! 개발 도중 마주한 이슈를 해결하기 위해 필요했던 log라면, 운영환경에서 예외발생을 대비한다는 관점에서는 유의미한 log일수 있기 때문일까요?
	- A :  임시로 디버깅을 하기 위해서는 System.out을 사용해도 괜찮지만, 개발 과정에서 이슈를 마주한 문제라면 나 혹은 팀원이 비슷한 실수를 할 확률이 높다는것이기 때문에 로그를 남기는것이 유의미함. 결국엔 log level을 관리하는게 더 좋은 방법. sout을 사용하면 개발 프로덕션과 테스팅 과정에서 받아보는 결과물이 달라질 수 있음. 개발 도중 마주한 이슈를 해결하기 위해 필요했던 log라면, 운영환경에서 **예외발생을 대비한다는 관점**에서는 **유의미한 log일수 있기 때문** O 단위테스트 등으로 해당 이슈를 막을 필요 존재
- Q 5 : 그렇다면, **현업에서는 어느정도의 수준까지 log를 관리하시는지** 궁금합니다..!(이러한 log관련해서 국내 혹은 국제적으로 표준이 있을까요?)
	- 표준은 없음. 가능한 많이, 되도록 폭팔하지 않게. get을 제외한 모든 api를 로그남기기도 함. 200대의 응답이 아닌 아닌 모든 응답을 남기는 경우도 있으며 그 양을 동적으로 조정함.
- Q 6 : 쿠버네티스나 Docker 와같은 가상환경에서 DB운영을 하는것은 DB의 본질과 맞지 않다는 이야기를 들었다. 로그를 가상환경 바깥으로 빼낸다던가, 혹은 백업을 가상환경 바깥으로 빼낸다는 전제하에 사용하는것도 좋지 않은것인가?
		A : 큰기업에서는 선호하지 않는다고 알고있다. 인프라 as code라고 코드를 통해 인프라 환경을 구성한다는것은 실수를 만들기 쉽다. + DB성능을 온전히 낼 수 없다는 한계점도 있다. 하지만 비용적인 면에서의 유리함이 놓칠 수 없는 부분이기에 스타트업에서는 많이들 도전하고있다. 

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 