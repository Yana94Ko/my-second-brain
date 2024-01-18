---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 13일차 (데이터베이스, SQL)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "242"
tistoryPostUrl: https://yanacoding.tistory.com/242
---
오늘 수강한 강의 : [【한글자막】 데이터 역량 강화를 위한 SQL 부트캠프](https://www.udemy.com/course/best-sql-2022/?utm_source=adwords&utm_medium=udemyads&utm_campaign=Webindex_Catchall_la.KR_cc.KR&utm_term=_._ag_154831691911_._ad_667917181863_._kw__._de_c_._dm__._pl__._ti_dsa-1456167871416_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA4smsBhAEEiwAO6DEjYTfA9uRKpohvXL57GOl1RtmvewP_qtbVoeZO3pIG1_bIILaS16QnRoCNZgQAvD_BwE)

---
# 오늘의 강의 정리 📗

# 데이터베이스란
- 데이터베이스란 여러 사람들이 공유하고 사용할 목적으로 통합 관리되는 `데이터들의 집합`
- 데이터를 `구조화`하여 저장함
- 효율적인 검색, 삽입, 업데이트 및 관리를 위해 조직되어짐.
# 왜 데이터베이스를 사용해야 하는가
## 파일 처리 시스템
- 문제점
	1. 중복 : 각 파일마다 필요한 데이터를 각각 가지고 있어야 하므로 전체적인 시간과 노력, 경제비용에 있어서 효율이 낮음
	2. 비일관성 : 데이터에 변경사항이 조금만 있어도 각 파일에서 해당되는 데이터를 모두 변경해야 -> 한꺼번에 수정이 되지 않으면 데이터값이 서로 다름(비일관성)
	3. 응용프로그램 개발 문제
	4. 데이터 추가 및 검색 문제
## 데이터 베이스의 특징
1. 데이터의 독립성
	- 물리적 독립성 : 데이터베이스 크기를 늘리거나 성능 향상을 위해 데이터 파일을 늘리거나 새롭게 추가해도 관련 애플리케이션을 수정할 필요가 없음
	- 논리적 독립성 : 데이터베이스는 논리적인 구조로 다양한 애플리케이션의 논리적 요구를 만족시킴
2. 데이터의 무결성
	- 데이터는 여러 경로를 통해서 들어오는데, 데이터에서 발생하는 경우의 수를 방지하는 기능으로 데이터의 유효성을 검사해서 무결성을 구현
3. 데이터의 보안성
	- 인가된 사용자들만 데이터베이스나 데이터베이스 내에 자원을 접근할 수 있도록 계정 관리 또는 접근 권한을 설정
4. 데이터의 일관성
	- 연관된 정보를 논리적인 구조로 관리해서, 어떤 하나의 데이터만 변경했을 경우에 발생할 수 있는 불일치성을 배제
	- 또 작업 중에 일부 데이터만 변경되서 나머지 데이터와 일치하지 않는 경우를 방지
5. 데이터 중복의 최소화
	- 데이터를 통합해서 관리함으로써, 파일 시스템의 단점 중 하나인 자료의 중복과 데이터의 중복성 문제를 최소화
# CF) 데이터 베이스의 성능
## 디스크 I/O를 어떻게 줄이냐..!
### 1) SELECT 시에는 꼭 필요한 칼럼만 불러와
### 2) 조건 부여시, 가급적 기존 DB값에 별도의 연산을 걸지 않기
### 3) LIKE 사용시 %(와일드카드문자열)를 string 앞부분에 배치하지 않는 것이 좋음
#### full table scan을 막게 다른 형태의 조건절을 사용하는것이 효과적
### 4) SELECT DISTINCT, UNION DISTINCT와 같이 중복 값을 제거하는 연산은 최대한 사용하지 않아야
#### 중복 값을 제거하는 연산은 시간이 많이걸리기 때문
#### 대체) EXISTS
### 5) 같은 내용의 조건이라면, GROUP BY 연산 시에는 가급적 HAVING보다는 WHERE 절을 사용
#### having절은 group by구문 실행 이후, where절은 구문 실행 전단계에서 필터링을 하기 때문

### 6) 3개 이상의 테이블을 INNER JOIN 할 때는, 크기가 가장 큰 테이블을 FROM 절에 배치하고, INNER JOIN 절에는 남은 테이블을 작은 순서대로 배치
#### INNER JOIN 과정에서 최소한의 Combination을 탐색하도록 FROM & INNER JOIN의 순서를 배열하면 좋다는 의미이지만, 항상 통용되지는 않음
### 7) 자주 사용하는 데이터의 형식에 대해서는 미리 전처리된 테이블을 따로 보관, 관리하는것도 좋음

# 다양한 DB 플랫폼
[![](https://i.imgur.com/aU6WfHF.png)](https://www.udemy.com/course/best-sql-2022/?utm_source=adwords&utm_medium=udemyads&utm_campaign=Webindex_Catchall_la.KR_cc.KR&utm_term=_._ag_154831691911_._ad_667917181863_._kw__._de_c_._dm__._pl__._ti_dsa-1456167871416_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA4smsBhAEEiwAO6DEjYTfA9uRKpohvXL57GOl1RtmvewP_qtbVoeZO3pIG1_bIILaS16QnRoCNZgQAvD_BwE)<center>이미지 출처 : 【한글자막】 데이터 역량 강화를 위한 SQL 부트캠프</center>
- 그중에서 이번 강의에서는 PostgreSQL을 사용하기러 함
	- 오픈소스(무료)
	- 많이 사용되는 플랫폼
	- 멀티 플랫폼이기 때문에 윈도우나 맥 등 다양한 환경에서 사용 가능
	- 설치가 매우 쉬운편

# SQL(Structured Query Language)
- 다양한 DB나 SQL 기반 소프트웨어에서 사용 할 수 있음

[![](https://i.imgur.com/uwROqJf.png)](https://www.udemy.com/course/best-sql-2022/?utm_source=adwords&utm_medium=udemyads&utm_campaign=Webindex_Catchall_la.KR_cc.KR&utm_term=_._ag_154831691911_._ad_667917181863_._kw__._de_c_._dm__._pl__._ti_dsa-1456167871416_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA4smsBhAEEiwAO6DEjYTfA9uRKpohvXL57GOl1RtmvewP_qtbVoeZO3pIG1_bIILaS16QnRoCNZgQAvD_BwE)<center>* 이미지 출처 : 【한글자막】 데이터 역량 강화를 위한 SQL 부트캠프</center>

# Brew를 통한 PostgreSQL 설치
### PostgreSQL 설치
```shell
//버전 명시하지 않음
brew install postgresql
//버전 명시
brew install postgresql@15
```
### PostgreSQL 설치버전 확인
```shell
postgres --version
postgres -V
```
### PostgreSQL brew로 실행
```shell
//버전 명시
brew services start postgresql@14

//버전 명시하지 않음(deprecated)
brew services start postgresql
```
### PostgreSQL psql (postgresql 쉘) 접속 : `psql postgres`
```shell
➜  ~ psql postgres
psql (14.10 (Homebrew))
Type "help" for help.

postgres=#
```
### PostgreSQL user 및 권한 확인 : `\du`
```shell
postgres=# \du

                                   List of roles
 Role name |                         Attributes                         | Member of
-----------+------------------------------------------------------------+-----------
 yanako    | Superuser, Create role, Create DB, Replication, Bypass RLS | {}

(END)
```
### PostgreSQL 사용자 생성 및 권한 추가
```shell
CREATE ROLE {사용자명} WITH LOGIN PASSWORD '{비밀번호}'; 
ALTER ROLE {사용자명} CREATEDB; // DB 생성 권한 부여
```
#### brew로 설치하는 경우, 일반 설치시와 다르게 default user가 postgres가 아닌 현재 로그인된 mac username로 생성되기 때문에, tar파일을 통해 DB를 restore하는 강의를 따라가기 위해서는 아래와 같은 설정이 필요하다.
```shell
CREATE ROLE postgres WITH LOGIN PASSWORD '비밀번호'; 
ALTER ROLE postgres CREATEDB; // DB 생성 권한 부여
```
- 설정 완료시
```postgresql
                                   List of roles
 Role name |                         Attributes                         | Member of
-----------+------------------------------------------------------------+-----------
 postgres  | Create DB, Replication                                     | {}
 root      | Superuser, Create DB, Replication                          | {}
 yanako    | Superuser, Create role, Create DB, Replication, Bypass RLS | {}

(END)
```
# SQL
[![](https://i.imgur.com/5j8WGNa.png)](https://www.udemy.com/course/best-sql-2022/?utm_source=adwords&utm_medium=udemyads&utm_campaign=Webindex_Catchall_la.KR_cc.KR&utm_term=_._ag_154831691911_._ad_667917181863_._kw__._de_c_._dm__._pl__._ti_dsa-1456167871416_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA4smsBhAEEiwAO6DEjYTfA9uRKpohvXL57GOl1RtmvewP_qtbVoeZO3pIG1_bIILaS16QnRoCNZgQAvD_BwE)<center>이미지 출처 : 【한글자막】 데이터 역량 강화를 위한 SQL 부트캠프</center>
## SELECT
```sql
SELECT column_name1, column_name2 FROM table_name;
```
- DB는 뒤에서 부터 읽음
	- 어느 테이블을 읽을건지 확인 한 뒤
	- 어느 컬럼을 읽어올지 확인
## SELECT 기본 형식
```sql
SELECT column_name1, column_name2, AGG()       -- 보여줄 컬럼 선택
	FROM table_name                            -- 조회할 테이블 명시
	WHERE condition1                           -- 필터링1(Group by 연산 전)
	GROUP BY column_name1                      -- 카테고리화
	HAVING condition2                          -- 필터링2(Group by 연산 후)
	ORDER BY column_name1 DESC, AGG() ASC      -- 정렬
	LIMIT n;                                   -- 갯수 제한
```
### * : 모든 값 조회
- 모든 값을 다 읽어올 때 사용
```sql
SELECT * FROM table_name;
```
- 자동으로 모든 내용이 쿼리되기 대문에, DB 트래픽을 증가시킬 수 있으며 조회 응답을 느리게 할 수 있기 때문에 가능한 지양하는것이 좋음
### WHERE : 특정 조건 조회
- 조회 해온 값 들 중에서 특정 조건의 값만 보일 때 사용
```sql
SELECT column_name1 FROM table_name WHERE conditions;
```
#### conditions 조건문
```sql
SELECT column_name1, column_name2 FROM table_name 
	WHERE column_name1 = 'example_value1' 
		AND column_name2 = 'example_value1';
```
##### 비교 연산자
| 연산자 | 설명 |
| ---- | ---- |
| = | 같다 |
| > | 크다 |
| < | 작다 |
| >= | 크거나 같다 |
| <= | 작거나 같다 |
| <> or != | 같지 않다(PostgreSQL 기준) |
##### 논리 연산자
| 연산자 | 설명 |
| ---- | ---- |
| AND | 그리고 |
| OR | 또는 |
| NOT | 해당 조건이 treu가 아니다 |

#### WHERE + BETWEEN & NOT BETWEEN 연산자
##### BETWEEN
- 특정 구간 내의 레코드를 열람할 때 사용
- `value >= low AND value <= high`와 같은 역할
```sql
SELECT cloumn_name1, column_name2 FROM table_name
	WHERE column_name1 BETWEEN low AND high;
```
##### NOT BETWEEN 연산자
- `value < low OR value > high`와 같은 역할
```sql
SELECT cloumn_name1, column_name2 FROM table_name
	WHERE column_name1 NOT BETWEEN low AND high;
```
##### DATE 연산자와 함께 사용 할 때에 유용
```sql
SELECT writeDate, column_name2 FROM table_name
	WHERE writeDate BETWEEN '2023-01-01' AND '2023-12-31';
```

#### WHERE + IN & NOT IN 연산자
##### IN
- 옵션 목록 안에 해당 값이 있는 경우에만 반환 할 때 사용
- `value = option1 OR value = option2 OR .,`와 같은 역할
```sql
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 IN (option1, option2.,);
```
##### NOT IN
- 옵션 목록 안에 해당 값이 없는 경우에만 반환 할 때 사용
- `value != option1 AND value != option2 AND .,`와 같은 역할
```sql
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 NOT IN (option1, option2.,);
```

#### WHRER + LIKE & ILIKE 연산자
##### 문자열 패턴
###### % : 모든 문자
- 해당 위치에 문자가 존재하지 않거나, 혹은 숫자 문자 빈칸 등 모든 형태의 문자가 존재함을 의미
###### _ : 한 글자
- 해당 위치에 문자가 1글자 존재함을 의미
##### LIKE : 대소문자 구분하면서 문자열 조회
```sql
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 LIKE 'A'; //column_name1의 value가 A인 레코드만 조회
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 LIKE 'A%';//column_name1의 value가 A로 시작하는 레코드만 조회
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 LIKE '%a';//column_name1의 value가 a로 끝나는 레코드만 조회
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 LIKE '_A%';//column_name1의 value가 아무 문자 1글자와 A로 시작하는 레코드만 조회
```
##### ILIKE :  대소문자를 구분하지 않으면서 문자열 조회
```sql
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 LIKE 'A'; //column_name1의 value가 A인 레코드만 조회
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 LIKE 'A%';//column_name1의 value가 A로 시작하는 레코드만 조회
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 LIKE '%a';//column_name1의 value가 a로 끝나는 레코드만 조회
SELECT column_name1, column_name2 FROM table_name
	WHERE column_name1 LIKE '_A%';//column_name1의 value가 아무 문자 1글자와 A로 시작하는 레코드만 조회
```
### ORDER BY : 특정 column 기준 정렬
- 조회해온 값을 특정 컬럼 기준으로 오름차순/내림차순 정렬해 보여줄 때 사용
```sql
//ORDER BY : column_name1 (default) 오름차순
SELECT column_name1, column_name2 FROM table_name ORDER BY column_name1;

//ORDER BY 컬럼명 ASC: column_name1 오름차순
SELECT column_name1, column_name2 FROM table_name 
	ORDER BY column_name1 ASC;

//ORDER BY 컬럼명 DESC: column_name1 내림차순
SELECT column_name1, column_name2 FROM table_name 
	ORDER BY column_name1 DESC;

//복합 조건 : column_name1 내림차순, column_name2 오름차순
SELECT column_name1, column_name2 FROM table_name 
	ORDER BY column_name1 DESC, column_name1 ASC;
```
### DISTINCT : 중복 제거
- 조회해온 값들에서 중복된 값을 제거 할 때 사용
```sql
SELECT DISTINCT column_name1, column_name2 FROM table_name;
```
### COUNT : 개수 세기
- 해당 조건에 맞게 조회된 값의 갯수를 표현 할 때 사용
```sql
SELECT COUNT(column_name1) FROM table_name;
SELECT COUNT(column_name2) FROM table_name;
SELECT COUNT(*) FROM table_name;
```
- 위의 쿼리문들은 모두 같은 값을 반환함. 
	- table_name에서 해당 조회를 하더라도 반환하는 레코드의 갯수는 똑같기 때문

#### COUNT의 경우 WHERE 혹은 DISTINCT등 조건 조회문과 함께 사용할때 유용
```sql
SELECT COUNT(DISTINCT column_name1) FROM table_name;
SELECT COUNT(column_name2) FROM table_name WHERE conditions;
```
### LIMIT : 조회 레코드 갯수 제한하기
#### 상위 순위 레코드 조회에 사용하기 좋음
- 지정한 갯수(n)개 만큼의 자료만 보여줌
```sql
SELECT column_name1 FROM table_name
	LIMIT n;
```
- ORDER BY와 함께 사용하면 상위순위 혹은 하위순위 레코드만 조회 할 수 있음
	- cf) n을 1로 설정하면 최상위, 최하위 레코드만 반환 가능
```sql
SELECT column_name1, column_name2 FROM table_name
	ORDER BY column_name1 DESC
	LIMIT n;
```
#### 페이징에 사용 할 수 있음
- 지정한 위치(m)부터, 지정한 갯수(n)개 만큼의 자료만 보여줌
```sql
SELECT column_name1 FROM table_name
	LIMIT m, n;
```

## DATE
### Timezone
- UTC : 세계 표준시
- Local Time Zone : 지역 시간대
	- 데이터를 사용자에게 표시할 때 사용자의 지역 시간대로 변환하여 제공하는 것이 일반적
```sql
show timezone; -- 만약 UTC 라는 문구가 보이면, timezone 세팅이 안된 상태

-- UTC 라는 문구가 보이면 일단 아래쿼리를 돌려보세요.
-- 아마 현재 보고 계신 시간(한국 기준)에서 -9:00 시간의 차이가 보일 겁니다.
select now();

-- timezone 세팅
-- 방법1: 하나의 세션에 대한 세팅
set timezone TO 'Asia/Seoul'; 

-- 방법2: Database 의 default timezone 세팅(설정 후 세션 재접속 필요)
ALTER DATABASE 데이터베이스_명 SET timezone TO 'Asia/Seoul';


-- 방법3: 하나의 계정에 대한 default timezone 세팅
ALTER USER 계정_명 SET timezone='Asia/Seoul' ;

-- 선택할 수 있는 timezone 열람
SELECT * FROM pg_timezone_names;
```
### DATE()
- timestamp 등으로 입력된 날짜값은 날짜 뿐 아니라 시간과 분 초까지 기록됨.
- 따라서 출력시에는 포매팅이 필요함
	- 관련해서 내일 강의에서 자세히 다룰 예정임으로 오늘은 DATE()만 다룸
- DATE(timestamp or datetime) : 타임스탬프나 datetime에서 날짜까지만 뽑아냄
```sql
SELECT DATE(columne_name1) FROM table_name
```

# SHOW TABLES? SHOW DATABASES?
## PostgreSQL 에서는 위와같이 DB목록이나 table목록을 조회하는 쿼리를 제공하지 않는다.
## SHOW DATABASES 대체
### pqsl 콘솔 사용 조회법
```
//일반 조회
\list
\l

//상세 조회
\list+
\lt+
```
### 쿼리 사용법
```sql
SELECT datname FROM pg_database -- 전체 데이터베이스 조회
SELECT datname FROM pg_database WHERE datistemplate = false -- 사용자가 생성한 데이터베이스만 조회
```

## SHOW TABLES 대체
### pqsl 콘솔 사용 조회법
```
\dt
\c databases_name
```
### 쿼리 사용법
```sql
select nspname from pg_catalog.pg_namespace -- 현재 db의 전체 스키마 조회
select tablename from pg_tables -- 전체 테이블 조회
```
# 도전과제

## 1. How many payment transactions were greater than $5.00?
- 정답 : 3,618
```sql
select count(amount) from payment
	where amount > 5;
```
![](https://i.imgur.com/lBeFYPS.png)
## 2. How many actors have a first name that starts with the letter P?
- 정답 : 5
```sql
SELECT COUNT(first_name) FROM actor
	WHERE first_name ILIKE 'P%';
```

![](https://i.imgur.com/L1Q13ZM.png)

## 3. How many unique districts are our customers from?
- 정답 : 378
```sql
SELECT COUNT(DISTINCT district) from address;
```
![](https://i.imgur.com/R3uAm4q.png)
## 4. Show unique district list form our customers address
```sql
SELECT DISTINCT district from address;
```
![](https://i.imgur.com/CYiAayU.png)
## 5. How many films have a rating of R and a replacement cost between $5 and $15?
- 정답 : 52
```sql
SELECT COUNT(*) from film
	WHERE rating = 'R'
	AND replacement_cost BETWEEN 5 AND 15;
```
![](https://i.imgur.com/C9S2UAI.png)

## 6. How many films have the word Truman somewhere in the title?
- 정답 : 5
```sql
SELECT COUNT(*) from film
	WHERE title LIKE '%Truman%';
```
![](https://i.imgur.com/cMn0y97.png)

---
# GROUP BY
## [집계 함수](https://www.postgresql.org/docs/9.5/functions-aggregate.html)
- 집계 함수는 SELECT 절이나 HAVING 절에서만 호출.
### AVG() - 평균
- 유의할 점 - 소숫점 자리가 긴 부동 소숫점을 반환
### ROUND() - 반올림
```
ROUND(숫자, 반올림할 자릿수)
```
### TURNCATE() - 버림
```
TURNCATE(숫자, 버릴 자릿수)
```
### COUNT() - 행의 갯수 반환
### MAX() - 최대값
### MIN() - 최소값
### SUM() - 합계
## GROUP BY
1. FROM문 바로 뒤 혹은 WHRER문 바로 뒤에 옴
	- 후자 : GROUP BY 실행하기 전에 WHERE문으로 데이터를 필터링 하는 것
2. GROUP BY문을 사용하고, 특정 column_name을 SELECT하는 경우에는, GROUP BY 구문에 해당 column_name을 반드시 포함시켜야 함.
```sql
//(X)
SELECT column_name1, column_name2, AGG(data_col)
	FROM table_name
	GROUP BY column_name1;
//(O)
SELECT column_name1, column_name2, AGG(data_col)
	FROM table_name
	GROUP BY column_name1,column_name2;
```
3. WHERE문에 집계함수를 입력하면 안 됨.
	- 해당 역할은 HAVING 절에서 처리되어야 함
4. GROUP BY 구문과 ORDER BY 구문을 동시에 사용하는 경우, 정렬의 기준이 될 값은 SELECT 구문 어딘가에 존재해야 함
```sql
SELECT company, SUM(sales)
	FROM finance_table
	GROUP BY company
	ORDER BY sum(sales);
```
### GROUP BY 동작 방식
#### 1. 카테고리가 될 열 선택
| ***Category*** | Data Value |
| ---- | ---- |
| ***A*** | 10 |
| ***A*** | 5 |
| ***B*** | 2 |
| ***B*** | 4 |
| ***C*** | 12 |
| ***C*** | 6 |
```sql
SELECT catagory_name1, catagory_name2 FROM table_name
	GROUP BY catagory_name1 
```
#### 2. 테이블을 카테고리별로 분류
| ***Category*** | Data Value |
| ---- | ---- |
| ***A*** | 10 |
| ***A*** | 5 |

| ***Category*** | Data Value |
| ---- | ---- |
| ***B*** | 2 |
| ***B*** | 4 |

| ***Category*** | Data Value |
| ---- | ---- |
| ***C*** | 12 |
| ***C*** | 6 |
#### 3. 집계 함수를 사용해 활용
```sql
SELECT catagory_name1, AGG(data_col) 
	FROM table_name
	GROUP BY catagory_name1
```
- AGG에 집계 함수(SUM(), COUNT(), AVG().,)사용
```sql
// company 별, division별 sales의 총액을 반환
SELECT company, division, SUM(sales)
	FROM finance_table
	WHERE company != 'Acompany'
	GROUP BY company, division
	ORDER BY SUM(sales) DESC
	LIMIT 1;
```

# 도전과제
## 1. We have two staff members, with Staff ID 1 and 2. We want to give a bonus to the staff member that handled the most payments.(Most in terms of number of payments processed, not total dollar amount). How many payments did each staff member handle and who gets the bonus?
- 정답 : 2번 스태프, 1번 2번 스태프 각각 7292, 2703회 판매
```sql
SELECT staff_id, COUNT(payment_id), 
(
	SELECT staff_id as winner
	FROM payment
	GROUP BY staff_id
	LIMIT 1
)		
	FROM payment
	GROUP BY staff_id;
```
![](https://i.imgur.com/MH3tOxL.png)

## 2. Corporate HQ is conduction a study on the relationship between replacement cost and a movie MPAA rating(e.g G, PG, R, ect...). What is average replacement cost per MPAA rating?
- 정답 : 사진첨부 참조
```sql
SELECT rating, ROUND(AVG(replacement_cost), 2)
	FROM film
	GROUP BY rating;
```
![](https://i.imgur.com/ELWqeYG.png)
## 3. We are running a promotion to reword our top 5 customers with coupons. What are the customer ids of the top 5 customers by total spend?
- 정답 : 148, 526, 178, 137, 144
```sql
SELECT customer_id FROM payment
	GROUP BY customer_id
	ORDER BY SUM(amount) DESC
	LIMIT 5;
```
![](https://i.imgur.com/JYpcI4A.png)


---
# 오늘의 멘토링 🥸
- Q1 : 프론트 엔드와 백엔드 개발자 간 흔히 발생하는 갈등 상황의 대표적인 케이스가 존재한다면 몇가지 소개를 부탁드립니다!
	- A : 이거 프론트에서 해주면 안되요? 이거 백엔드에서 해주면 안되요? 라고 하는 분업에서 충돌이 일어남. 따라서 최근에는 [Graphql](https://tech.kakao.com/2019/08/01/graphql-basic/)과 같은 방법들을 사용하는 추세.
- Q2 : 백엔드 개발자 관점에서, 프론트엔드 개발자와 원활히 협업하기 위해 가지면 좋을 마인드셋이나 배경지식이 있을까요?
	- A : 나와 협업하는 사람이 어떤 일을 해야하는지 아는것이 좋은 것 같다. 직접 해보는것을 추천한다. 프론트엔드를 구현해본다던가, DBA를 이해하기 위해 DB 작업을 해본다던가 하는 등.

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 