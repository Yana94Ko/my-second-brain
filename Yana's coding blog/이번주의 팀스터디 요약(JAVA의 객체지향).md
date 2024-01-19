---
tistoryBlogName: yanacoding
tistoryTitle: 이번주의 팀스터디 요약(SQL, JAVA 코딩테스트)
tistoryVisibility: "3"
tistoryCategory: "1197248"
tistorySkipModal: true
tistoryPostId: "245"
tistoryPostUrl: https://yanacoding.tistory.com/245
---
# 👱‍♀ 자머니조의 팀스터디 🥊

# 이번주의 팀스터디 - 자바의 객체지향 (Feat 자바의 정석)
## 객체 - 클래스와 메서드
## 생성자
## 상속 - 인터페이스 추상클래스 추상메서드
## 패키지, 제어자, 접근 제어자, 캡슐화

![](https://i.imgur.com/MYmppyY.png)


---
# 월요일 : 클래스와 메서드
1. 클래스와 객체의 관계에 대해 이해하기.
2. 클래스의 구성 요소가 변수와 메서드인 점 이해하기
3. static변수와 비 static변수, 지역변수가 사용되는 위치와 범위 그리고 상황에 대해서 알아보기
4. 가능하다면 각 변수들이 저장되는 공간에 대해서 한번 알아보기
5. static 메서드와 비static메서드가 사용되는 상황에 대해 알아보기

![](https://i.imgur.com/zT7isJj.jpg)


---
# 화요일 : 생성자(Feat 붕어빵 틀)

![](https://i.imgur.com/l1Ry0WW.png)

![](https://i.imgur.com/bRRVeSg.png)

---
# 수요일 : 상속 - 인터페이스 추상클래스 추상메서드

![](https://i.imgur.com/QTjV41u.png)

## 실제 프로젝트 내에서 사용되는 예시를 통한 이해
- BaseEntity라는 abstract 클래스를 구현하고
```java
import java.sql.Timestamp;
import java.time.LocalDateTime;

import org.springframework.data.annotation.CreatedDate;
import org.springframework.data.annotation.LastModifiedDate;
import org.springframework.data.jpa.domain.support.AuditingEntityListener;

import jakarta.persistence.EntityListeners;
import jakarta.persistence.MappedSuperclass;
import lombok.Getter;

@Getter
@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class BaseEntity {
	@CreatedDate
	private LocalDateTime createdAt;

	@LastModifiedDate
	private LocalDateTime updatedAt;
}
```

- Entity에서 상속받아서 사용하면, createdAt과 updatedAt이 필요한 엔티티에는 공통적으로 넣을 수 있다!
```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.util.ArrayList;
import java.util.List;

import org.springframework.boot.context.properties.bind.DefaultValue;

import growth.soft.jobconsulting.global.entity.BaseEntity;
import jakarta.persistence.Column;
import jakarta.persistence.ElementCollection;
import jakarta.persistence.Entity;
import jakarta.persistence.EnumType;
import jakarta.persistence.Enumerated;
import jakarta.persistence.FetchType;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.OneToMany;
import jakarta.validation.constraints.Size;
import lombok.AccessLevel;
import lombok.Getter;
import lombok.NoArgsConstructor;

@Entity
@NoArgsConstructor(access = AccessLevel.PROTECTED)
@Getter
public class User extends BaseEntity {
	//내용
}

```

- JPARepository는 extends받아와서 너무 편하게 DB를 다룰 수 있다!
```java
import java.util.Optional;

import org.springframework.data.jpa.repository.JpaRepository;

import growth.soft.jobconsulting.domain.entity.User;

public interface UserRepo extends JpaRepository<User, Long> {
	Integer countUserByEmail(String email);
	Optional<User> findByEmail(String email);
	Optional<User> findByEmailAndPassword(String email, String password);
}

```

---
# 목요일 : 패키지, 제어자, 접근 제어자, 캡슐화

![](https://i.imgur.com/oKjfVtz.png)

![](https://i.imgur.com/FfmeTvF.png)

## 실제 프로젝트 내에서 사용되는 예시를 통한 이해
- JWT Property의 final, static
```java
package yana.playground.security.jwt;  
  
public class JwtProperties {  
	public static final int EXPIRATION_TIME = 6000; //600초  
	public static final String COOKIE_NAME = "jwt"  
;}
```
- Entity 의 private 요소들
```java
import java.util.ArrayList;
import java.util.List;

import growth.soft.jobconsulting.global.entity.BaseEntity;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.OneToMany;
import jakarta.validation.constraints.Size;
import lombok.AccessLevel;
import lombok.Getter;
import lombok.NoArgsConstructor;

@Entity
@NoArgsConstructor(access = AccessLevel.PROTECTED)
@Getter
public class Company extends BaseEntity {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;
	@Size(max = 7)
	private String code;
	@Size(max = 15)
	private String name;
	@OneToMany(mappedBy = "company")
	private List<Program> programList = new ArrayList<>();

}

```

---
# 금요일 : 객체지향 프로그래밍 코드 짜보기

![](https://i.imgur.com/ULLDjAD.png)
![](https://i.imgur.com/Y9N1jQ1.png)
## 아들러의 코드
```java
import java.util.Scanner;

class Day {
    private String work; // 하루 할 일을 나타내는 문자열
    public void set(String work) {this.work = work;}
    public String get() {return work;}
    public void show() {
        if (work == null) System.out.println("없습니다.");
        else System.out.println(work + "입니다.");
    }
}

public class MonthSchedule {
    private Day[] days;
    private Scanner scanner;

    public MonthSchedule(int dayCount) {
        days = new Day[dayCount];
        for (int i = 0; i < dayCount; i++) {
            days[i] = new Day();
        }
        scanner = new Scanner(System.in);
    }

    public void run() {
        System.out.println("이번달 스케줄 관리 프로그램.");
        while (true) {
            printMenu();
            int command = scanner.nextInt();
            switch (command) {
                case 1:
                    input();
                    break;
                case 2:
                    view();
                    break;
                case 3:
                    finish();
                    return;
                default:
                    System.out.println("잘못된 입력입니다. 다시 입력해주세요.");
            }
        }
    }

    private void printMenu() {
        System.out.println("할 일 (입력:1, 보기:2, 끝내기:3) >> ");
    }

    private void input() {
        System.out.println("날짜(1~30)? ");
        int day = scanner.nextInt();
        if (day < 1 || day > 30) {
            System.out.println("잘못된 날짜입니다.");
            return;
        }
        System.out.print("할 일(빈칸 없이 입력)? ");
        String work = scanner.next();
        days[day - 1].set(work);
    }

    private void view() {
        System.out.print("날짜(1~30)? ");
        int day = scanner.nextInt();
        if (day < 1 || day > 30) {
            System.out.println("잘못된 날짜입니다.");
            return;
        }
        System.out.println(day + "일의 할 일은 " + days[day - 1].get() + "입니다.");
    }

    private void finish() {
        System.out.println("프로그램을 종료합니다.");
    }

    public static void main(String[] args) {
        MonthSchedule schedule = new MonthSchedule(30);
        schedule.run();
    }
}
```

## 야나의 객체지향 코드
```java
package growth.soft.jobconsulting;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.time.LocalDateTime;
import java.util.Arrays;

class Day {
	private String work; // 하루의 할 일을 나타내는 문자열
	public void set(String work) { this.work = work; }
	public String get() { return work; }
	public void show() {
		if (work == null) System.out.println("없습니다.");
		else System.out.println(work + "입니다.");
	}
}


class MonthSchedule {
	final int days;
	Day[] taskList;
	int faultCnt = 0;
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));


	MonthSchedule(int days){
		this.days = days;
		this.taskList = new Day [days];
		Arrays.fill(this.taskList,new Day());
	}
	public void run() throws IOException {
		System.out.print("이번달 스케쥴 관리 프로그램.\n할일(입력:1, 보기:2, 끝내기:3) >>");

		int userChoice = 0;

		while (userChoice==0){
			userChoice = getIntFromUser();
		}

		while (true){
			switch (userChoice) {
				case 1 -> {
					input();
					faultCnt = 0;
				}
				case 2 -> {
					view();
					faultCnt = 0;
				}
				case 3 -> {
					finish();
					faultCnt = 0;
				}
				default -> {
					faultCnt++;
					System.out.println("잘못 입력하셨습니다. 다시 시도하세요.(실패 횟수 : " + faultCnt + ", 3회 실패시 종료)\n");
					if(faultCnt > 3){
						finish();
					}
					run();
				}
			}
		}

	}
	private void input() throws IOException {
		System.out.print("날짜(1~30)? ");
		int date = 0;
		while (date==0){
			date = getIntFromUser();
		}

		System.out.print("할일(빈칸없이입력)? ");
		String task = br.readLine();
		taskList[date].set(task);

		System.out.println();
		reRunAfterOneSecond();
	}
	private void view() throws IOException {
		System.out.print("날짜(1~" + days + ")? ");
		int date = 0;
		while (date==0){
			date = getIntFromUser();
		}

		System.out.print(date + "일의 할 일은 ");
		taskList[date].show();

		System.out.println();
		reRunAfterOneSecond();
	}
	private void finish() throws IOException {
		System.out.println("프로그램을 종료합니다.");
		br.close();
		System.exit(0);
	}
	private int getIntFromUser() throws IOException {
		int intValue = 0;
		try {
			intValue = Integer.parseInt(br.readLine());
		} catch (NumberFormatException e) {
			System.out.println("잘못된 입력 입니다. 숫자를 입력하세요");
		}
		return intValue;
	}
	private int getIntFromUserRangeCheck() throws IOException {
		int userInput = getIntFromUser();
		boolean checked = false;
		while(!checked){
			if(userInput > days){
				System.out.println("없는 날짜입니다. 날짜 범위 내에서 다시 입력해주세요.(날짜 범위 : 1 ~ "+days+"일)");
				getIntFromUser();
			}else {
				checked = true;
			}
		}
		return userInput;
	}
	private void reRunAfterOneSecond() throws IOException {
		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		run();
	}

}
public class Main {
	public static void main(String[] args) throws IOException {
		MonthSchedule april = new MonthSchedule(30);
		april.run();
	}
}
```

## 코코의 객체지향 코드
```java
package teamStudy.MonthSchedule;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

class IndexException extends RuntimeException {

	public IndexException(String msg) {
		super(msg);
		System.out.println(msg);
	}

	public IndexException() {
		System.out.println("인덱스 오류 범위입니다.");
	}
}

public class MonthSchedule {
	private int maxDay;
	private ArrayList<Day> arrayDaySchedule;
	private Scanner Scanner = new Scanner(System.in);

	MonthSchedule(int maxDay) {
		this.maxDay = maxDay;
		this.arrayDaySchedule = new ArrayList<>(Collections.nCopies(maxDay, new Day()));
	}

	public void input() {
		System.out.printf("날짜(%d~%d):", 1, maxDay).println();
		int myDay = Scanner.nextInt();

		if (myDay < 0 || myDay > 30) {
			throw new IndexException("유효하지 않은 날짜입니다.");
		}

		try {
			Scanner.nextLine();
			System.out.println("할일(빈칸없이입력)");
			String work = Scanner.nextLine();
			arrayDaySchedule.set(myDay - 1, new Day());
			arrayDaySchedule.get(myDay - 1).set(work);
		} catch (IndexOutOfBoundsException e) {
			e.printStackTrace();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	public void view() {
		System.out.printf("날짜(%d~%d):", 1, maxDay).println();
		int myDay = Scanner.nextInt();

		if (myDay < 0 || myDay > 30) {
			throw new IndexException("유효하지 않은 날짜입니다.");
		}

		try {
			arrayDaySchedule.get(myDay - 1).show();
		} catch (IndexOutOfBoundsException e) {
			e.printStackTrace();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	public void finish() {
		System.out.println("종료");
		Scanner.close();

	}

	public void run() {
		System.out.println("이번달 스케줄 관리 프로그램");
		while (true) {
			System.out.println("할일(입력:1, 보기:2, 끝내기:3)");
			int menu = Scanner.nextInt();
			switch (menu) {
			case 1:
				input();
				break;

			case 2:
				view();
				break;
			case 3:
				finish();
				return;
			default:
				System.out.println("다시 입력해주세요");
				break;

			}
		}

	}
}
```

## MZ의 객체지향 코드
```java
import java.util.Scanner;

public class ScheduleManager {
    private Day[] schedule;

    public ScheduleManager() {
        this.schedule = new Day[30]; // 30일까지의 스케쥴을 저장하는 배열
    }

    // 할일 추가
    public void input(int day, String todo) {
        if (day < 1 || day > 30) {
            System.out.println("잘못된 날짜입니다.");
            return;
        }
        
        Day dayObj = new Day();
        dayObj.set(todo);
        schedule[day - 1] = dayObj;
    }

    // 할일 조회
    public void view(int day) {
        if (day < 1 || day > 30) {
            System.out.println("잘못된 날짜입니다.");
            return;
        }

        Day dayObj = schedule[day - 1];
        if (dayObj != null) {
            System.out.print(day + "일의 할 일은 ");
            dayObj.show();
        } else {
            System.out.println(day + "일에 등록된 할 일이 없습니다.");
        }
    }

    // 프로그램 종료
    public void finish() {
        System.out.println("프로그램을 종료합니다.");
        System.exit(0);
    }

    // 실행
    public void run() {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.print("할일(입력1 보기2 끝내기3) >> ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("날짜(1~30) ? ");
                    int dayInput = scanner.nextInt();
                    scanner.nextLine(); // 버퍼 비우기
                    System.out.print("할일(빈칸없이입력) ? ");
                    String todoInput = scanner.nextLine();
                    input(dayInput, todoInput);
                    break;
                case 2:
                    System.out.print("날짜(1~30) ? ");
                    int dayView = scanner.nextInt();
                    view(dayView);
                    break;
                case 3:
                    finish();
                    break;
                default:
                    System.out.println("잘못된 입력입니다. 다시 입력해주세요.");
            }
        }
    }

    public static void main(String[] args) {
        ScheduleManager scheduleManager = new ScheduleManager();
        scheduleManager.run();
    }
}

class Day {
    private String work; // 하루의 할 일을 나타내는 문자열

    public void set(String work) {
        this.work = work;
    }

    public String get() {
        return work;
    }

    public void show() {
        if (work == null)
            System.out.println("없습니다.");
        else
            System.out.println(work + "입니다.");
    }
}
```

---
# 이번주 우리팀의 팀스터디 회고
## MZ의 회고 
자바를 학습한지 어느새 열흘인데 하루하루 배울수록 어렵게 느껴졌다. 코드는 둘째치고 개념을 이해하기도  많이 어려웠는데, 조원들 덕분에 어느정도 이해하는데 도움이 많이 되었다. 앞으로도 많은 도움 받겠습니다.
## 야나의 회고
팀원들에게 설명하면서 나 스스로도 다시 한 번 자바를 이해하고 넘어갈 수 있어서 좋았고,
실제 프로젝트에서 사용하는 모습들을 보여주면서, 평소에 무의식적으로 사용하던 자바의 특성을 다시 한번 짚을 수 있어 좋았다!
팀원들이 좋아해서 더 좋았다!
## 아들러의 회고
자바를 오랜만에 공부해서 어려웠다.  
하지만 현아님 특강 덕분에 이해가 쏙쏙 됐다. 특히 붕어빵으로 클래스 상속 인스턴스 메소드를 알려주는 부분은 압권이었다. 현아님을 메가스터디로!
## 코코의 회고
팀원의 프로젝트를 통해서 배운 개념이 어떻게 쓰이는지 배우고, 예제를 직접 구현해 볼 수 있어서 좋았습니다!