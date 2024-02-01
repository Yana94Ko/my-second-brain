---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 24일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "263"
tistoryPostUrl: https://yanacoding.tistory.com/263
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
## 자바 프로그래밍의 스레드와 동시성
### 스레드 개념
#### 프로세스(process)
단순히 실행중인 프로그램이라고 할 수 있음. 즉, 사용자가 작성한 프로그램이 운영체제에 의해 메모리 공간을 할당받아 실행중인 것을 말함. PID를 찾아 해당 process를 kill한것을 생각하면 기억하기 쉬울 것.

이러한 프로세스는 프로그램에 사용되는 데이터와 메모리 등의 자원, 그리고 스레드로 구성됨
#### 스레드(thread)
프로세스 내에서 실제로 작업을 수행하는 주체. 모든 프로세스는 한 개 이상의 스레드가 존재하여 작업을 수행. 또한 두 개 이상의 스레드를 가지는 프로세스를 멀티스레드 프로세스라고 부름.

### 자바에서 스레드의 생성과 실행
#### Thread 클래스 상속
```java
class ThreadWithClass extends Thread {
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(getName()); // 현재 실행 중인 스레드의 이름을 반환함.
            try {
                Thread.sleep(10);          // 0.01초간 스레드를 멈춤.
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```
Thread클래스를 상속받으면 다른 클래스를 상속 받을 수 없으므로, 일반적으로 Runnable 인터페이스를 구현하는 방법으로 스레드 생성.
#### Runnable 인터페이스 구현
```java
class ThreadWithRunnable implements Runnable {
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getName()); // 현재 실행 중인 스레드의 이름을 반환함.
            try {
                Thread.sleep(10);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```
#### 스레드의 실행
```java
public class Thread01 {
    public static void main(String[] args){
        ThreadWithClass thread1 = new ThreadWithClass();       // Thread 클래스를 상속받는 방법
        Thread thread2 = new Thread(new ThreadWithRunnable()); // Runnable 인터페이스를 구현하는 방법

        thread1.start(); // 스레드의 실행
        thread2.start(); // 스레드의 실행
    }
}
```
#### 실행 결과
```java
Thread-0
Thread-1
Thread-0
Thread-1
Thread-0
Thread-1
Thread-0
Thread-1
Thread-0
Thread-1
```
### 스레드의 우선순위
|필드|설명|
|---|---|
|static int MAX_PRIORITY|스레드가 가질 수 있는 최대 우선순위를 명시함.|
|static int MIN_PRIORITY|스레드가 가질 수 있는 최소 우선순위를 명시함.|
|static int NORM_PRIORITY|스레드가 생성될 때 가지는 기본 우선순위를 명시함.|
getPriority()와 setPriority() 메소드를 통해 스레드의 우선순위를 반환하거나 변경할 수 있음. 하지만 스레드의 우선순위는 비례적인 절댓값이 아닌 어디까지나 상대적인 값.
### 스레드의 JOIN
스레드에서 특정 스레드의 종료까지 대기하도록 하기 위한 메서드
```java
import java.util.ArrayList;

public class Sample extends Thread {
    int seq;
    public Sample(int seq) {
        this.seq = seq;
    }

    public void run() {
        System.out.println(this.seq+" thread start.");
        try {
            Thread.sleep(1000);
        }catch(Exception e) {
        }
        System.out.println(this.seq+" thread end.");
    }

    public static void main(String[] args) {
        ArrayList<Thread> threads = new ArrayList<>();
        for(int i=0; i<10; i++) {
            Thread t = new Sample(i);
            t.start();
            threads.add(t);
        }

        for(int i=0; i<threads.size(); i++) {
            Thread t = threads.get(i);
            try {
                t.join(); // t 쓰레드가 종료할 때까지 기다린다.
            }catch(Exception e) {
            }
        }
        System.out.println("main end.");
    }
}

```

## 자바 프로그래밍의 예외처리
### 예외 클래스
![](https://i.imgur.com/evwRyJ9.png)
#### RuntimeException : 실행 시 발생하는 예외
주로 치명적인 예외 상황을 발생시키지 않는 예외들로 구성. 예외를 처리하는것도 좋지만, 프로그램을 작성하면서 예외가 발생하지 않도록 주의를 기울이는 편이 좋음.
#### 그 외의 Exception 클래스의 자식 클래스 : 컴파일 시 발생하는 예외
보통 치명적인 예외 상황을 발생시키므로, 반드시 예외를 처리해야함. 따라서 자바 컴파일러는 RuntimeException 클래스 이외의 Exception 클래스의 자식 클래스에 속하는 예외가 발생할 가능성이 있는 구문에는 반드시 예외를 처리하도록 강제함.
#### Exception은 예측이 가능한 경우에 사용하고, RuntimeException은 발생할 수도 있고 발생하지 않을 수도 있는 경우에 사용
#### 자주 사용되는 예외 클래스
|클래스|설명|
|---|---|
|ClassCastException|수행할 수 없는 타입 변환이 진행될 경우|
|ArrayIndexOutOfBoundsException|배열에 잘못된 인덱스를 사용하여 접근할 경우|
|NullPointerException|null 객체의 인스턴스 메소드를 호출하는 등의 경우|
|ArithmeticException|산술 연산에서 정수를 0으로 나누는 등 연산을 수행할 수 없는 경우|
### try ~ catch
```java
try {
    <수행할 문장 1>;
    <수행할 문장 2>;
    ...
} catch(예외1) {
    <수행할 문장 A>;
    ...
} catch(예외2 | 예외3) {
    <수행할 문장 a>;
    ...
}
```
try 문 안의 수행할 문장 중에서 예외가 발생하지 않는다면 catch 문에 속한 문장들은 수행되지 않음. 
#### finally - 예외와 상관 없이 수행되어야 하는 경우 사용
예시 상황 : 외부로의 connection을 연 경우, 예외가 발생하더라도 connection은 닫아주어야한다.
```java
try {
    <수행할 문장 1>;
    <수행할 문장 2>;
    ...
} catch(예외1) {
    <수행할 문장 A>;
    ...
} catch(예외2) {
    <수행할 문장 a>;
    ...
} finally {
	<반드시 수행되어야 하는 문장>
}
```
### throw
메서드 내에서 예외를 발생시키는 데 사용됨.(예: `throw new FoolException()`)
### throws
 메소드 선언부에 사용해서 메소드를 사용 할 때 발생 할 수 있는 예외를 미리 명시하는 효과가 있으며, 동시에 해당 메서드가 처리하지 않은 예외를 호출자에게 전달함을 나타냄.(예: `public void sayNick(String nick) throws FoolException`)
```java
public class Sample {
    public void sayNick(String nick) throws FoolException {
        try {   // try .. catch 문을 삭제할수 있다.
            if("바보".equals(nick)) {
                throw new FoolException();
            }
            System.out.println("당신의 별명은 "+nick+" 입니다.");
        }catch(FoolException e) {
            System.err.println("FoolException이 발생했습니다.");
        }
    }

    public static void main(String[] args) {
        Sample sample = new Sample();
        sample.sayNick("바보");
        sample.sayNick("야호");
    }
}

```
### try-with-resources - Java SE 7
사용한 자원을 자동으로 해제해줌. 아래와 같이 try 블록에 괄호(())를 추가하여 파일을 열거나 자원을 할당하는 명령문을 명시하면, 해당 try 블록이 끝나자마자 자동으로 파일을 닫거나 할당된 자원을 해제해 줌.
```java
try (파일을열거나자원을할당하는명령문) {
     ...
}
```
#### 파일 읽기 예제
#### try-with-resources 사용 예시
```java
static String readFile(String filePath) throws IOException {
    BufferedReader br = new BufferedReader(new FileReader(filePath));
    try {
        return br.readLine();
    } finally {
        if (br != null)
            br.close();
    }
}
```

#### try-with-resources 미사용 예시 - Java SE 7 이전
```java
static String readFile(String filePath) throws IOException {
    try (BufferedReader br = new BufferedReader(new FileReader(filePath))) {
        return br.readLine();
    }
}
```

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 