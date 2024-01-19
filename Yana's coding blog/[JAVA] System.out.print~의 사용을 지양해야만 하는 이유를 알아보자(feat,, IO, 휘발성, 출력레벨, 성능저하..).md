---
tistoryBlogName: yanacoding
tistoryTitle: "[JAVA] System.out.print~의 사용을 지양해야만 하는 이유를 알아보자(feat,, IO, 휘발성, 출력레벨, 성능저하..)"
tistoryTags: sysout,System.out,java.util.Logging,Log4j,Logback,Log4j2,Slf4J,java,io,I/O,블로킹
tistoryVisibility: "3"
tistoryCategory: "1032871"
tistorySkipModal: true
tistoryPostId: "249"
tistoryPostUrl: https://yanacoding.tistory.com/249
---
&emsp;사실 전부터 'System.out.print()를 사용하면 성능에 좋지 않고 logger가 조금 더 프로젝트 내부에서 출력을 하는 목적에 맞으니 logger를 사용해보세요'라는 피드백을 받고 "System.out의 사용을 지양해야겠구나"라고는 생각하였으나 제대로 파헤쳐 보지 못했는데, 오늘 JAVA교육 수강 중 System.out이 나와 이참에 "**대체 왜 System.out은 운영 및 개발환경에서 사용을 지양해야하는지**" 알아보고자 한다.
<br/>
&emsp;`+[게시글 작성 마무리 작업 중 추가하는 한 마디]` 한번 제대로 파헤쳐보니, 왜 System.out의 사용을 지양해야하는지 이해가 가기 시작했다. 습관적으로, 그리고 logging 프레임워크를 불러와 사용하기 귀찮다는 이유로, 디버깅 상황에서 Sout을 호출하던 습관을 이번 기회에 버릴 수 있을 것 같다.
&emsp;사실 아직도 주관적으로는 "운영환경이 아닌 개발환경에서 임시로 디버깅을 하기 위해서는 System.out을 사용해도 괜찮지 않을까?"하는 생각을 가지고있긴 하지만, 서버를 운영하며 마주할 여러 예외의 상황에서 제대로 이슈의 원인을 파악하기 위해서는 log 레벨을 조정한다 하더라도 이미 기존에 한 번 발생했던 이슈에 관한 log는 남기는것이 맞다는 생각도 든다.(현업에서는 이 모든 상황에 대해 log를 만들며 개발을 하고계실까? 궁금하다.)
> 멘토님의 답변 : "현업에서 로그는 가능한 많이, 폭발하지는 않게."
---
# 0. Logging이 대체 뭔데?
## Logging이란?
- 서비스 동작 시 시스템 상태, 작동 정보를 시간의 경과에 따라 기록하는 것을 말함

## Logging을 하는 이유는?
- 서비스의 동작 상태를 파악하거나, 발생한 장애를 알려주는 등 "파악하기 위해서" 사용
- 추가적으로, 테스팅 코드와 운영 코드를 동일하게 가져가면서 로깅을 선언적으로 관리할 수 있고, 운영시 성능 오버헤드를 최소화할 수 있는 메커니즘이 필요하다고 함.
	- 이러한 필요성에 의해 우리는 이번 글에서 왜 System.out의 사용을 지양해야하는지 살펴보고자 함

## JAVA 프로그래밍에서 Logging을 사용하는 방법
### 1. Linux System API(sysout)
- (java의 system call을 받는 주체..? 확인이 필요하다)
### 2. JAVA API(System.out.~)
- 기초적으로 많이 사용하는 console 출력방식
### 3. JAVA API(util.Logging) : jul
- 자바 1.4부터 기본적으로 제공하는 로깅 유틸리티
	- 1.4버전부터 제공을 해왔는데, 왜 사람들은 sout을 기본적으로 많이 사용할까?
### 4. 각종 Logging 프레임워크 사용
1. Log4j(Apache, 2015년 8월을 마지막으로 개발 중단 -> Log4j2로 업그레이드 권장)
2. Log4j2(Apache, 이번 게시글에서는 sout을 Log4j2와 주로 비교해보려 한다.)
3. Logback(Log4j를 개선하기 위해 개발. 멀티 스레드 환경 등에서 Log4j2가 우세, 비동기 Logging 시 Parameterized Message Formating 비용 증가 등의 면모로 인해 현재는 Log4j2를 많이 사용한다고 한다.)
	1) 그렇다면 왜 Spring Framework의 기본 logger는 Log4j2가 아닌 logback일까?
		-> Log4j가 2015년에 지원이 중단되고, spring-boot-starter-logging이 2014년에 지원된 것으로 미루어 보아 당시엔 logback이 더 발전된 프레임워크가 아니었을까 추측
		-> 기존에 logback을 사용하던 프로젝트들의 유연한 마이그레이션을 제공하기 위해서는 logback을 지원하는쪽이 유리했기 때문이 아닐까..?
4. Slf4J(여러 로그 프레임워크를 위한 API, 로그 프레임워크에 종속되지 않은 Logging 지원)

![](https://i.imgur.com/RyvyAOt.png)
<center href="https://www.atatus.com/blog/best-practices-in-java-logging/">[출처] https://www.atatus.com/blog/best-practices-in-java-logging/</center>

- 관련해서 다른 포스팅에서 각각의 logging 프레임워크도 다뤄볼까 한다.

---
# 1. 성능 이슈(오버헤드 다량)
## I/O로 인한 시스템콜과 커널모드, 블러킹
- System.out과 System.error은 내부적으로 시스템콜을 호출함.
	- I/O를 하고 싶으면 커널이 가지고 있는 function을 호출
	- 운영체제는 해당 작업을 처리하기 위해 user모드에서 커널 모드로 변경한뒤 run
	- 해당 과정이 블로킹으로 호출됨 -> 해당 I/O가 발생하는 작업시간 동안 CPU가 놀게됨
	- -> 성능저하로 이어짐.
## synchronized 메서드
- System.out 이나 System.error 메서드 둘 다 write()와 newLine()을 사용
	- 해당 메서드는 내부적으로 synchronized 키워드를 이용해서 구현되어 있음.
	- 멀티 스레드 환경에서 사용시 해당 모니터락 객체를 점유한 스레드 이외의 스레드는 대기해야함.
	- ex) spring 을 실행하며 tomcat 은 max thread 200 개를 갖게 됨
		- 만약 thread 1 에서 lock 을 획득하여 print 하게 되면,
		- 나머지 199개는 print 를 하기 위해 lock 을 획득할 때 까지 기다려야 할 것.
## 즉, _System_._out_.println() 호출은 디스크 I/O동안 동기화(synchronized)처리가 되므로 시스템의 throughput을 떨어뜨림

---
# 2. 로그 출력레벨 분리의 한계
## System.out 및 System.err(2단계)
### System.out
```java
System.out.println("This is an informational message");
```
### System.err
```java
System.err.println("This iss an error message");
```
## Log4J2 로깅(6단계 - trace, debug, info, error, warn, fatal)
```java
logger.trace("Trace log message");
logger.debug("Debug log message");
logger.info("Info log message");
logger.error("Error log message");
logger.warn("Warn log message");
logger.fatal("Fatal log message");
```
---
# 3. 휘발성 - 파일에 로그 쓰기
## System.out 및 System.err 재 라우팅
```java
//System.out 라우팅
PrintStream outStream = new PrintStream(new File("outFile.txt"));
System.setOut(outStream);
System.out.println("This is a routing out log");
```
```java
//System.err 라우팅
PrintStream errStream = new PrintStream(new File("errFile.txt"));
System.setErr(errStream);
System.err.println("This is a routing error log");
```
- System.out 또는 System.err을 사용하여 추렭을 파일로 리디섹션 할 대, 파일 크기를 제어할 수 없음.
	- 즉, 응용프로그램이 실행되는 동안 파일이 계속 커짐
	- 파일이 커지면, 더 큰 로그를 열어나 분석하기 어려울 수 있음
### + System.out 혹은 System.error로 생성한 콘솔 로그를 출력 파일로 리다이렉트 할 지라도, 어플리케이션 서버가 재 시작할 때 파일이 overwrite될 수도 있음.

## Log4J2로 파일에 로깅
- 파일에 로그를 체계적으로 작성하고, 특정 정책에 따라 파일을 롤링하는 매커니즘 제공
1.  **날짜 / 시간 패턴을 기반으로 롤오버 할 파일을 구성 할 수 있음**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="INFO">
    <Appenders>
        <File name="fout" fileName="log4j/target/baeldung-log4j2.log"
          immediateFlush="false" append="false">
            <PatternLayout pattern="%d{yyyy-MM-dd HH:mm:ss} %p %m%n"/>
        </File>
    <Loggers>
        <AsyncRoot level="DEBUG">
            <AppenderRef ref="stdout"/>
            <AppenderRef ref="fout"/>
        </AsyncRoot>
    </Loggers>
</Configuration>
```
2. **주어진 임계값에 도달하면 크기에 따라 파일을 롤링 할 수 있음**
```xml
...
<RollingFile name="roll-by-size"
  fileName="target/log4j2/roll-by-size/app.log" filePattern="target/log4j2/roll-by-size/app.%i.log.gz"
  ignoreExceptions="false">
    <PatternLayout>
        <Pattern>%d{yyyy-MM-dd HH:mm:ss} %p %m%n</Pattern>
    </PatternLayout>
    <Policies>
        <OnStartupTriggeringPolicy/>
        <SizeBasedTriggeringPolicy size="5 KB"/>
    </Policies>
</RollingFile>
```
## 즉 logging 그중에서도 logging 프레임워크들을 사용하면, 로그 파일을 편리하게 관리 할 수 있다.
---

# 결론 및 추가 학습 방향
## System.out의 사용은 성능저하와 오버헤드, 휘발성, 로그 레벨 분리의 제한 등의 이유로 인해, 운영환경에서 사용을 지양해야 한다.

그렇다면, 어떤 로깅 프레임워크를 사용하는게 좋을까? 관련해서는 다른 포스팅에서 살펴보고자 한다

