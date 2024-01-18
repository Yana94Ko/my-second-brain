---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 15일차 (SQL 조건문과 프로시저)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "246"
tistoryPostUrl: https://yanacoding.tistory.com/246
---
오늘 수강한 강의 : [【한글자막】 데이터 역량 강화를 위한 SQL 부트캠프](https://www.udemy.com/course/best-sql-2022/?utm_source=adwords&utm_medium=udemyads&utm_campaign=Webindex_Catchall_la.KR_cc.KR&utm_term=_._ag_154831691911_._ad_667917181863_._kw__._de_c_._dm__._pl__._ti_dsa-1456167871416_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA4smsBhAEEiwAO6DEjYTfA9uRKpohvXL57GOl1RtmvewP_qtbVoeZO3pIG1_bIILaS16QnRoCNZgQAvD_BwE)

---
# 오늘의 강의 정리 📗

# Data types
- Postgresql의 데이터 타입 [참조](https://www.postgresql.org/docs/current/datatype.html)
# 제약조건(Constraints)
## 컬럼 제약조건
- NOT NULL: 해당 null 값이 들어갈 수 없다
- UNIQUE: 해당 컬럼에는 중복되는 값이 들어갈 수 없다
- PRIMARY KEY : 기본키 UNIQUE + NOT NULL 의 결합과 같음
- FOREIGN KEY : 기본키를 참조하는 컬럼 or 컬럼들의 집합 (외래키는 **기본키나 유니크가 아니면 생성 제약**)
- REFERENCES: Foreign key 에서 참조되는 테이블의 이름은 REFERENCES 키워드 다음에 명시
- CHECK: 컬럼의 값을 어떤 특정 범위로 제한
- EXCLUSION: ?
## 테이블 제약조건
- CHECK (condition): 컬럼의 값을 어떤 특정 범위로 제한
- UNIQUE (column_list): 중복된 값 허용 X
- PRIMARY KEY (column_list): 기본키 UNIQUE + NOT NULL 의 결합과 같음
## SERIAL
- sequence를 만들어서 자동으로 1씩 증가하는 값으로 채워주는 data type
- PK 컬럼에 쓰기 딱 좋음
- SERIAL 컬럼에는 따로 INSERT를 해주지 않아도 된다

# DATABASE의 생성과 수정 삭제
## CREATE Database
```sql
CREATE DATABASE IF NOT EXISTS my_database;
```
## ALTER DATABASE
- 보통의 경우 이러한 변경은 허용되지 않음.
## DROP DATABASES
```sql
DROP DATABASE IF EXISTS my_database;
```

# TABLE의 생성과 수정 삭제
## CREATE Table
```sql
CREATE TABLE [IF NOT EXISTS] table_name (
   column1 datatype(length) column_contraint,
   column2 datatype(length) column_contraint,
   column3 datatype(length) column_contraint,
   table_constraints
);
```
## INSERT
```sql
INSERT INTO table_name(column1, column2, …)
VALUES (value1, value2, …);
``` 
## UPDATE
```sql
UPDATE t1
SET t1.c1 = new_value
FROM t2
WHERE t1.c2 = t2.c2;
```
## DELETE
```sql
DELETE FROM table_name
WHERE condition;
```

## ALTER Table
- IF EXISTS 키워드 활용 가능
```sql
ALTER TABLE table_name action;
```

## DROP Table
```sql
DROP TABLE [IF EXISTS] table_name 
[CASCADE | RESTRICT];
```

# CASE문 : 여러가지 조건 준 반환할 값을 선택
```sql
CASE
	WHEN 조건1 THEN 
		SQL 문장들1
	WHEN 조건2 THEN
		SQL 문장들2
	WHEN 조건3 THEN
		SQL 문장들3
	ELSE
		SQL 문장들4
END;
```
# NULL과 관련된 함수
## NULL 의 특성
- 아직 정의되지 않은 값으로 0 또는 공백과 다르다. (0은 숫자이고, 공백은 문자다)
- 테이블을 생성할 때 NOT NULL 또는 PRIMARY KEY로 정의되지 않으면 NULL을 포함할 수 있다. 
- NULL을 포함하는 연산의 결과도 NULL이다 ( 1 + NULL = NULL) 
    - 컬럼 A가 1 이고 컬럼 B가 NULL 일때는 연산 결과가 NULL 이지만, 
    - 컬럼 A에서 숫자 1과 NULL 이 있는 상태에서 sum(A)를 하면 NULL 을 제외한 1값이 나온다. 
- NULL과 연산하고 싶을 때에는 시스템에서 의미 없는 문자로 바꿔서 연산하는 경우가 많다. 혹은 NVL 함수를 이용할 수도 있다.
## NULLIF문 : 표현식이 서로 같으면 NULL, 다르면 표현식1반환
- 특정 값을 NULL로 변경해야 할 때 유용하게 사용 할 수 있음
```sql
NULLIF (표현식1, 표현식2);
```
## NVL / ISNULL : 표현식 1의 결과값이 NULL이면 표현식2 값 출력
- 표현식1과 표현식2의 결과 데이터 타입이 같아야 함.
- NULL 관련해서 가장 많이 사용되는 함수
```sql
-- 오라클: NVL (NULL 판단 대상, 'NULL일 때 대체값')
SELECT NVL(NULL, 'NVL-OK') NVL_TEST
FROM   DUAL ;
--결과값 : NVL-OK
```
```sql
-- sql server : ISNULL (NULL 판단 대상, 'NULL일 때 대체값')
SELECT ISNULL(NULL, 'NVL-OK') ISNULL_TEST
-- 결과값: NVL-OK
```
## COALESCE문 : 여러 인자 중 첫번째 not-null값 반환
- 임의의 개수 표현식에서 NULL이 아닌 최초의 표현식을 나타냄
- 모든 표현식이 NULL이라면 NULL을 리턴
```sql
COALESCE(value1, value2, ...);
```
# CAST문 : 데이터 유형을 다른 데이터 유형으로 변환
```sql
CAST([변환하고자 하는 값/컬럼] AS [목표 데이터 타입])
```

# Views : 가상 테이블
- 뷰는 실제 데이터를 가지고 있지 않으며 진짜 테이블에 링크된 개념
```sql
CREATE VIEW view_name1
  AS
	SELECT column_name1, column_name2, ...
	FROM table_name1
	WHERE conditions;
```
- 뷰의 삭제
```sql
DROP VIEW IF EXISTS view_name1;
```

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 