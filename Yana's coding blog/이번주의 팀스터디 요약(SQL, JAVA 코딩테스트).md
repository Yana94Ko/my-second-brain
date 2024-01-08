---
tistoryBlogName: yanacoding
tistoryTitle: 이번주의 팀스터디 요약(SQL, JAVA 코딩테스트)
tistoryVisibility: "3"
tistoryCategory: "1197248"
tistorySkipModal: true
tistoryPostId: "245"
tistoryPostUrl: https://yanacoding.tistory.com/245
---
# 준호생일축하해조의 팀스터디 🥊

# 이번주의 팀스터디 플랫폼 - 프로그래머스 [코딩테스트 SQL, JAVA](https://school.programmers.co.kr/learn/challenges)

---
# 월요일 : 🌅 즐거운 새해 첫 날 🌅

---
# 화요일 : SQL - SELECT, GROUP BY 구문 연습
## 1. [진료과별 총 예약 횟수 출력하기(GROUP BY)](https://school.programmers.co.kr/learn/courses/30/lessons/132202)
### 베니의 풀이
```sql
SELECT MCDP_CD AS '진료과코드', COUNT(APNT_YMD) AS '5월예약건수' FROM APPOINTMENT
WHERE APNT_YMD LIKE '%-05-%'
GROUP BY MCDP_CD
ORDER BY COUNT(APNT_YMD), MCDP_CD
```
### 코코의 풀이
```sql
SELECT MCDP_CD AS 진료과코드, COUNT(*) AS 5월예약건수
FROM APPOINTMENT
WHERE MONTH(APNT_YMD)=5
GROUP BY MCDP_CD
ORDER BY COUNT(*) ASC, MCDP_CD ASC;
```
### 알파카의 풀이
```sql
SELECT MCDP_CD AS '진료과 코드', COUNT(APNT_NO) AS '5월예약건수' FROM APPOINTMENT WHERE APNT_YMD  LIKE '%-05-%' GROUP BY MCDP_CD ORDER BY COUNT(APNT_NO),MCDP_CD
```
### 야나의 풀이
```sql
SELECT mcdp_cd as '진료과코드', COUNT(apnt_no) as'5월예약건수' FROM appointment
    WHERE apnt_ymd LIKE '2022-05%'
    GROUP BY mcdp_cd
    ORDER BY COUNT(apnt_no) ASC, mcdp_cd ASC;
```
## 2. [3월에 태어난 여성 회원 목록 출력하기(SELECT)](https://school.programmers.co.kr/learn/courses/30/lessons/131120)

### 베니의 풀이
```sql
SELECT MEMBER_ID, MEMBER_NAME, GENDER, DATE_FORMAT(DATE_OF_BIRTH, '%Y-%m-%d') FROM MEMBER_PROFILE
WHERE DATE_OF_BIRTH LIKE '%-03-%'
AND GENDER='W' 
AND TLNO IS NOT NULL
ORDER BY MEMBER_ID;
```
### 코코의 풀이
```sql
SELECT MEMBER_ID, MEMBER_NAME, GENDER AS GENDER, DATE_FORMAT(DATE_OF_BIRTH,'%Y-%m-%d') AS DATE_OF_BIRTH
FROM MEMBER_PROFILE
WHERE MONTH(DATE_OF_BIRTH)=3 AND TLNO IS NOT NULL AND GENDER  ='W'
ORDER BY MEMBER_ID;
```
### 알파카의 풀이
```sql
SELECT MEMBER_ID, MEMBER_NAME,GENDER, DATE_FORMAT(DATE_OF_BIRTH, '%Y-%m-%d') AS DATE_FORMAT  FROM MEMBER_PROFILE WHERE TLNO IS NOT NULL AND GENDER='W' AND DATE_OF_BIRTH LIKE '%-03-%' ORDER BY MEMBER_ID;
```
### 야나의 풀이
```sql
SELECT member_id, member_name, gender, DATE_FORMAT(date_of_birth, '%Y-%m-%d') as date_of_birth
    FROM member_profile
    WHERE gender = 'W'
        AND MONTH(date_of_birth) = 3
        AND tlno IS NOT NULL
```
# 수요일 : String, Date타입 다루기, JOIN구문 연습
## 1.  [조회수가 가장 많은 중고거래 게시판의 첨부파일 조회하기(String, Date타입)](https://school.programmers.co.kr/learn/courses/30/lessons/164671)
### 베니의 풀이
```sql
SELECT CONCAT('/home/grep/src/',USED_GOODS_BOARD.BOARD_ID,'/',FILE_ID,FILE_NAME,FILE_EXT) AS FILE_PATH
FROM USED_GOODS_BOARD
INNER JOIN USED_GOODS_FILE
ON USED_GOODS_BOARD.BOARD_ID = USED_GOODS_FILE.BOARD_ID
WHERE USED_GOODS_BOARD.VIEWS = (SELECT MAX(VIEWS) FROM USED_GOODS_BOARD)
ORDER BY FILE_ID DESC
```
### 코코의 풀이
```sql
SELECT CONCAT('/home/grep/src/',USED_GOODS_BOARD.BOARD_ID,'/',FILE_ID,FILE_NAME,FILE_EXT) AS STR FROM USED_GOODS_BOARD
INNER JOIN USED_GOODS_FILE
ON USED_GOODS_BOARD.BOARD_ID = USED_GOODS_FILE.BOARD_ID
WHERE VIEWS = (SELECT MAX(VIEWS) FROM USED_GOODS_BOARD)
ORDER BY STR DESC;
```
### 알파카의 풀이
```sql
SELECT CONCAT('/home/grep/src/',USED_GOODS_FILE.BOARD_ID,'/',FILE_ID,FILE_NAME,FILE_EXT ) AS FILE_PATH
FROM USED_GOODS_FILE
INNER JOIN USED_GOODS_BOARD
ON USED_GOODS_FILE.BOARD_ID = USED_GOODS_BOARD.BOARD_ID
WHERE VIEWS = (SELECT MAX(VIEWS) FROM USED_GOODS_BOARD)
ORDER BY FILE_ID DESC
```
### 야나의 풀이
```sql
SELECT CONCAT('/home/grep/src/',tBoard.board_id,'/',tFile.file_id, tFile.file_name, tFile.file_ext) AS 'FILE_PATH'
    FROM used_goods_file tFile
    JOIN used_goods_board tBoard
    ON tFile.board_id = tBoard.board_id
    WHERE tBoard.views = (
        SELECT MAX(views)
            FROM used_goods_board
    )
    ORDER BY tFile.file_id DESC;
```
## 2. [있었는데요 없었습니다(JOIN)](https://school.programmers.co.kr/learn/courses/30/lessons/59043)
### 베니의 풀이
```sql
SELECT ANIMAL_INS.ANIMAL_ID, ANIMAL_INS.NAME FROM ANIMAL_INS
INNER JOIN ANIMAL_OUTS
ON ANIMAL_INS.ANIMAL_ID = ANIMAL_OUTS.ANIMAL_ID
WHERE ANIMAL_INS.DATETIME > ANIMAL_OUTS.DATETIME
ORDER BY ANIMAL_INS.DATETIME
```
### 코코의 풀이
```sql
SELECT ANIMAL_INS.ANIMAL_ID, ANIMAL_INS.NAME FROM ANIMAL_INS
INNER JOIN ANIMAL_OUTS
ON ANIMAL_INS.ANIMAL_ID = ANIMAL_OUTS.ANIMAL_ID
WHERE ANIMAL_INS.DATETIME > ANIMAL_OUTS.DATETIME
ORDER BY ANIMAL_INS.DATETIME;
```
### 알파카의 풀이
```sql
SELECT ANIMAL_INS.ANIMAL_ID,ANIMAL_INS.NAME FROM ANIMAL_INS INNER JOIN ANIMAL_OUTS ON ANIMAL_INS.ANIMAL_ID = ANIMAL_OUTS.ANIMAL_ID
WHERE ANIMAL_OUTS.DATETIME < ANIMAL_INS.DATETIME ORDER BY ANIMAL_INS.DATETIME
```
### 야나의 풀이
```sql
SELECT tOut.animal_id, tOut.name FROM animal_outs tOut
    JOIN animal_ins tIn
        ON tOut.animal_id = tIn.animal_id
    WHERE tOut.datetime < tIn.datetime
    ORDER BY tIn.datetime;
```
# 목요일 : SQL 최고 난이도 문제 풀이
## 1. [상품을 구매한 회원 비율 구하기(서브쿼리, WITH)](https://school.programmers.co.kr/learn/courses/30/lessons/131534)
### 베니의 풀이
```sql
SELECT YEAR(SALES_DATE) AS YEAR, MONTH(SALES_DATE) AS MONTH, COUNT(DISTINCT(USER_INFO.USER_ID)) AS PUCHASED_USERS, ROUND(COUNT(DISTINCT(USER_INFO.USER_ID)) / (SELECT COUNT(*) FROM USER_INFO WHERE YEAR(JOINED) = 2021), 1) AS PUCHASED_RATIO
FROM USER_INFO
INNER JOIN ONLINE_SALE
ON ONLINE_SALE.USER_ID = USER_INFO.USER_ID
WHERE YEAR(JOINED) = 2021
GROUP BY MONTH(SALES_DATE)
ORDER BY YEAR(SALES_DATE), MONTH(SALES_DATE)
```
### 코코의 풀이
```sql
SELECT YEAR(SALES_DATE) AS YEAR, MONTH(SALES_DATE) AS MONTH,COUNT(DISTINCT(ONLINE_SALE.USER_ID)) AS PUCHASED_USERS, 
ROUND(COUNT(DISTINCT(ONLINE_SALE.USER_ID))/(SELECT COUNT(USER_ID)FROM USER_INFO WHERE YEAR(JOINED)=2021),1)
FROM USER_INFO
RIGHT JOIN ONLINE_SALE
ON USER_INFO.USER_ID =  ONLINE_SALE.USER_ID
WHERE YEAR(JOINED) = 2021
GROUP BY YEAR(SALES_DATE),MONTH(SALES_DATE)
ORDER BY YEAR(SALES_DATE),MONTH(SALES_DATE)
```
### 알파카의 풀이
```sql
SELECT
  EXTRACT(year FROM SALES_DATE) AS year,
  EXTRACT(month FROM SALES_DATE) AS month,
  COUNT(DISTINCT (USER_INFO.USER_ID)) AS PURCHASED_USERS,
ROUND(COUNT(DISTINCT (USER_INFO.USER_ID))
     /(SELECT COUNT(USER_INFO.USER_ID) FROM USER_INFO WHERE YEAR(JOINED) = '2021'),1)
    AS PUCHASED_RATIO
FROM USER_INFO
INNER JOIN ONLINE_SALE
  ON USER_INFO.USER_ID = ONLINE_SALE.USER_ID
WHERE YEAR(JOINED) = '2021' AND SALES_AMOUNT > 0
GROUP BY year, month
ORDER BY year,month
```
### 야나의 풀이(WITH 써보기 🌟)
```sql
WITH user_2021 AS(
    SELECT * FROM user_info
    WHERE YEAR(joined) = '2021'
)
SELECT
    YEAR(o.sales_date) AS YEAR
    ,MONTH(o.sales_date) AS MONTH
    ,COUNT(DISTINCT u.user_id) AS PUCHASED_USERS
    ,ROUND(COUNT(DISTINCT u.user_id)
         /(
             SELECT COUNT(*) FROM user_2021
         ), 1) AS PUCHASED_RAITO
    FROM user_2021 AS u
    JOIN online_sale AS o
        ON o.user_id = u.user_id
    GROUP BY 
        YEAR, MONTH
    ORDER BY
        YEAR, MONTH;
```
# 금요일 : JAVA 
## 1.  [정수 제곱근 판별](https://school.programmers.co.kr/learn/courses/30/lessons/12934)
### 베니의 풀이
```java
class Solution {
    public long solution(long n) {
        long answer = -1;
        double x = Math.sqrt(n);
        if (x%1 == 0){
            answer = ((long)x+1) * ((long)x+1);
        }
        return answer;
    }
}
```
### 코코의 풀이
```java
class Solution {
    public long solution(long n) {
        if (n%Math.sqrt(n)==0){
            return (long)Math.pow((Math.sqrt(n)+1),2);
        }
        else{
            return -1;
        }
        
    }
}
```
### 알파카의 풀이
```java
class Solution {
    public static long solution(long n) {
        double sqrtN = Math.sqrt(n);
        long answer = 0;
        if (sqrtN % 1 != 0) { //나머지가 있다면 제곱근 X
            answer = -1;
        } else {
            answer = (long) Math.pow((sqrtN) + 1, 2);
        }
        return answer;
    }
}
```
### 야나의 풀이
#### (Math, Stream 활용 탐색... 저랑 자바로 코테 풀면서 노실분 9함)
```java
import java.util.stream.LongStream;

class Solution {
    public long solution(long n) {
        return (LongStream
            .range(1, (long) Math.sqrt(n)+1)
            .filter(v -> n % v ==0 && n/v == v)
            .count() != 0)
            ? (long) Math.pow( Math.sqrt(n) + 1, 2) : -1;
    }
}
class Solution {
    public long solution(long n) {
        return n % Math.sqrt(n) == 0 ? (long) Math.pow( Math.sqrt(n)+1,2) : -1;
    }
}
class Solution {
    public long solution(long n) {
        double sqrtN = Math.sqrt(n);
        return Math.floor(sqrtN) == sqrtN ? (long) Math.pow(sqrtN + 1, 2) : -1;
    }
}
```

---

# 회고
 - 베니 : 
	 - 그날 진도에 맞춰 SQL문제를 풀어볼 수 있어 좋았습니다. 쉬운 문제 위주로 풀긴 했지만, 문제를 맞추면서 SQL을 익혔다는 느낌이 들었습니다.  
	- 오늘 진도는 자바여서 자바문제를 풀었는데, 파이썬으로는 정말 쉬운 문제를 자바로 하려고 하니까 좀 힘들었습니다. 파이썬이 정말 좋은 것 같습니다.
 - 코코 : 
	 - 배운 내용을 응용해서 SQL문제를 풀어볼 수 있어서 좋았습니다. 오늘은 SQL말고 코딩테스트 문제를 풀었는데 못풀어서 더 연습을 해야겠다고 생각했습니다!
 - 알파카 : 
	 - 평소 SQL 문제를 따로 풀어볼 생각을 안해봤는데 이번에 같이 SQL 을 배우면서 진도에 맞는 문제를 푸니 즐거웠습니다~
 - 야나 : 
	 - 드디어 자바에 들어가서 너무 기쁩니다...
	 - SQL에서 다양한 함수를 사용하는 방법을 익히게 된 것 같아 좋았습니다!
<br/><br/><br/><br/><br/>
# 🥳🥳🥳🥳 준호님 생일축하합니다!!🥳🥳🥳🥳
![](https://i.imgur.com/29pMBCF.png)
