---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 14일차 (SQL)"
tistoryTags: 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "243"
tistoryPostUrl: https://yanacoding.tistory.com/243
---
오늘 수강한 강의 : [【한글자막】 데이터 역량 강화를 위한 SQL 부트캠프](https://www.udemy.com/course/best-sql-2022/?utm_source=adwords&utm_medium=udemyads&utm_campaign=Webindex_Catchall_la.KR_cc.KR&utm_term=_._ag_154831691911_._ad_667917181863_._kw__._de_c_._dm__._pl__._ti_dsa-1456167871416_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA4smsBhAEEiwAO6DEjYTfA9uRKpohvXL57GOl1RtmvewP_qtbVoeZO3pIG1_bIILaS16QnRoCNZgQAvD_BwE)

---
# 오늘의 강의 정리 📗
<목차여기>
# HAVING : 집계가 수행된 '이후'에 진행할 필터링
- AGG()와 같은 값(GROUP BY 이후 알게될 값)을 기준으로 필터링시 사용
	- cf) WHERE : 집계가 수행되기 전 실행할 필터링
- 따라서, GROUP BY절 뒤에 위치한다.
```sql
SELECT column_name1, column_name2, AGG()
	FROM table_name
	WHERE cloumn_name1 != "value"
	GROUP BY cloumn_name1
	HAVING AGG() conditions
```

# 도전과제
## 1. We are launching a platinum service for our most loyal customers. We will assign platinum status to customers that have had 40 or more transaction payments. What customer_ids are eligible for platinum status?
- 정답 : 144, 526, 148
```sql
SELECT customer_id
	FROM payment
	GROUP BY customer_id
	HAVING COUNT(payment_id) >= 40;
```
![](https://i.imgur.com/nj6ALfJ.png)

## 2. What are customer ids of customers who have spent more than $100 in payment transactions with our staff_id member 2?
- 정답 : 187, 522, 526, 211, 148
```sql
SELECT customer_id
	FROM payment
	WHERE staff_id = 2
	GROUP BY customer_id
	HAVING SUM(amount) > 100;
```
![](https://i.imgur.com/bRJCqI2.png)

# 평가시험1
## 1. ID가 2인 직원에게서 최소 110달러를 쓴 고객의 ID를 찾으십시오.
- 정답 : 187, 148
```sql
SELECT customer_id
	FROM payment
	WHERE staff_id = 2
	GROUP BY customer_id
	HAVING SUM(amount)>=110
```
![](https://i.imgur.com/5WYNvzY.png)

## 2. J로 시작하는 영화는 몇 편입니까?
- 정답 : 20편
```sql
SELECT COUNT(film_id)
	FROM film
	WHERE title LIKE 'J%';
```
![](https://i.imgur.com/KXsML1K.png)

## 3. 이름이 ‘E’로 시작하는 **동시에** 주소 ID가 500 미만인 고객 중, ID 번호가 가장 높은 고객은 누구입니까?
- 정답 : Eddie Tomlin
```sql
SELECT first_name || ' ' || last_name AS customer_name 
	FROM customer
	WHERE first_name LIKE 'E%'
		AND address_id < 500
	ORDER BY customer_id DESC
	LIMIT 1
```
![](https://i.imgur.com/Gw9UrUJ.png)

---
# ASLIAS : 별칭
- 특정 컬럼의 명칭을 바꾸어서 출력하거나,
- 연산(AGG())의 결과에 대한 명칭을 지정하거나, 
- JOIN등의 상황에서 사용
## AS문 : 별칭(alias) 생성기
- 쿼리의 맨 마지막에 실행됨
	- WHERE 연산자나 GOUP BY 호출에서는 별칭을 사용 할 수 없다는 의미
```sql
--(O)--
SELECT column_name1 AS new_name
	FROM table_name;
--(O)--
SELECT AGG() AS new_name
	FROM table_name;
--(X)--
SELECT column_name1, AGG() AS new_name
	FROM table_name
	GROUP BY column_name1
	HAVING new_name conditions;
--(O)--
SELECT column_name1, AGG() AS new_name
	FROM table_name
	GROUP BY column_name1
	HAVING AGG() conditions;
```

---
# JOINS : 데이터베이스 테이블 결합
![](https://i.imgur.com/pxnOH50.png)

## INNER JOIN(내부 조인) - JOIN의 default 값
- 두 테이블의 교집합
- 두 테이블을 연결할 때 가장 많이 사용
- 두 테이블 모두에서 발생하는 레코드만 조회
	- 비교의 기준이 되는 컬럼은 2번 반복됨. 따라서 중복되는 컬럼을 별칭을 통해 하나로 출력
- 두 테이블의 JOIN 기준이 되는 테이블을 서로 바꾸어도, 혹은 열 매칭 순서를 바꾸어도 같은 값을 반환한다.

![](https://i.imgur.com/H9gI0Ov.png)
![](https://i.imgur.com/wrF1Nar.png)
``` sql
SELECT * FROM table_name1
	INNER JOIN table_name2
		ON table_name1.column_name1 = table_name2.column_name2;

SELECT * FROM table_name2
	INNER JOIN table_name1
		ON table_name2.column_name2 = table_name1.column_name1;

SELECT *, column_name2 AS new_name FROM table_name2
	INNER JOIN table_name1
		ON table_name2.column_name2 = table_name1.column_name1;
```
## OUTER JOIN
### FULL OUTER JOIN
- 두 테이블의 합집합
- 존재하지 않는 컬럼 / 레코드는  null값으로 채워짐

![](https://i.imgur.com/kxA32jm.png)
![](https://i.imgur.com/AnSjVhP.png)
```sql
SELECT * FROM table_name1
	FULL OUTER JOIN table_name2
	ON table_name1.column_name1 = table_name2.column_name2;
```
#### FULL OUTER JOIN WHERE IS NULL
- 두 테이블의 차집합

![](https://i.imgur.com/TtwNPRV.png)
```sql
SELECT * FROM table_name1
	FULL OUTER JOIN table_name2
	ON table_name1.column_name1 = table_name2.column_name2
	WHERE table_name1.id IS NULL OR table_name2.id IS NULL;
```

### LEFT OUTER JOIN = LEFT JOIN
- 두 테이블에서 기준이되는 talble(FROM 테이블, left 테이블)에 있는 값들만 출력
- right 테이블에 있는 레코드 중 left 테이블에 없는 값은 생성되지 않으며
	- 더불어 left에 레코드가 존재하지만 right에는 존재하지 않는 경우 right의 컬럼은 null로 채워짐

![](https://i.imgur.com/n1EMzlP.png)
![](https://i.imgur.com/cOLZHMa.png)
```sql
SELECT * FROM tabla_name1
	LEFT OUTER JOIN table_name2
	ON table_name1.column_name1 = table_name2.column_name2;
```
#### LEFT OUTER JOIN WHIT right_table.id IS NULL
- left 테이블에만 존재하는 유니크 레코드를 뽑을 수 있음

![](https://i.imgur.com/vSPcGkq.png)
```sql
SELECT * FROM table_name1
	LEFT OUTER JOIN table_name2
	ON table_name1.column_name1 = table_name2.column_name2
	WHERE table_name2.id IS NULL;
```

### RIGHT OUTER JOIN = RIGHT JOIN
- 두 테이블에서 조인되는 talble(JOIN 테이블, right 테이블)에 있는 값들만 출력
 - left 테이블에 있는 레코드 중 right 테이블에 없는 값은 생성되지 않으며
	- 더불어 right에 레코드가 존재하지만 left에는 존재하지 않는 경우 left의 컬럼은 null로 채워짐

![](https://i.imgur.com/Qcc3w50.png)
![](https://i.imgur.com/NN16733.png)
```sql
SELECT * FROM table_name1
	RIGHT OUTER JOIN table_name2
	ON table_name2.column_name2 = table_name1.column_name1;
```
#### RIGHT JOIN WITH left_table.id IS NULL
- right 테이블에만 존재하는 유니크 레코드를 뽑을 수 있음

![](https://i.imgur.com/KPgxIUN.png)
```sql
SELECT * FROM table_name1
	RIGHT OUTER JOIN table_name2
	ON table_name2.column_name2 = table_name1.column_name1
	WHERE table_name1.id IS NULL;
```

---
# UNION
- 합칠 쿼리문들의 컬럼 명이 동일해야 한다
	- 동일하지 않은 경우 AS를 통해 맞춰주어야 함
- 쿼리문에서 출력할 컬럼의 개수와, 각각의 데이터타입 또한 동일해야 한다
## JOIN과의 차이점
- JOIN : 새로운 열로 결합(수평 결합)
- UNION : 새로운 행으로 결합(수직 결합)

![](https://i.imgur.com/NfZ8D3H.png)

## UNION
- 여러 쿼리문을 합쳐서 하나의 쿼리문으로 만들어주는 방법(중복 제거, 정렬 시도_완전정렬은 아님)
- 중복 제거 연산이 추가로 수행되기 때문에 UNION ALL보다 연산 속도가 느림
```sql
SELECT *, column_name1 FROM table_name1
UNION
SELECT *, column_name2 AS column_name1 FROM table_name2;
```
## UNION ALL
 - 여러 쿼리문을 합쳐서 하나의 쿼리문으로 만들어주는 방법(중복 허용)
- 중복 제거 연산이 수행되지 않아 UNION보다 연산 속도가 빠름
```sql
SELECT *, column_name1 FROM table_name1
UNION ALL
SELECT *, column_name2 AS column_name1 FROM table_name2;
```
## INTERSECT(Oracle, Maria : ok | Mysql : no)
- 두개의 테이블에서 겹치는 부분을 추출(교집합)
## EXCEPT(Maria : ok | Oracle = MINUS : ok | Mysql : no)
- 두개의 테이블에서 left 테이블에 unique하게 존재하는 컬럼만 조회
# SELF JOIN
- 자기 자신을 JOIN하는 방법
- alias를 통해 별칭을 지정해주어야함(같은 명칭의 테이블 명을 2번 반복하기 때문)
- inner join, outer join, cross join등 모든 조인이 가능

![](https://i.imgur.com/sv2g3sH.png)

```sql
SLELCT * FROM table_name1 t1
	JOIN table_name1 t2
	ON t1.column_name1 = t2.column_name2;
```

---
# JOIN 함수 연습문제
## 1. California sales tax laws have changed and we need to alert our customer to this through email. What are the emails of customers who lives in California?
- 정답 : "patricia.johnson@sakilacustomer.org","betty.white@sakilacustomer.org","alice.stewart@sakilacustomer.org","rosa.reynolds@sakilacustomer.org","renee.lane@sakilacustomer.org","kristin.johnston@sakilacustomer.org","cassandra.walters@sakilacustomer.org","jacob.lance@sakilacustomer.org","rene.mcalister@sakilacustomer.org".
```sql
SELECT email FROM customer
	JOIN address
	ON customer.address_id = address.address_id
	WHERE address.district = 'California';
SELECT customer.email FROM address
	JOIN customer
	ON customer.address_id = address.address_id
	WHERE district = 'California';
```
![](https://i.imgur.com/hx7OxVU.png)

## 2. A customer walks in and is a huge fan of the actor "Nick Wahlberg" and wants to know which movies he is in. Get a list of all movies "Nick Wahlberg" has been in.
- 정답 : Adaptation Holes, Apache Divine, Baby Hall, Bull Shawshank, Chainsaw Uptown, Chisum Behavior, Destiny Saturday, Dracula Crystal, Fight Jawbreaker, Flash Wars, Gilbert Pelican, Goodfellas Salute, Happiness United, Indian Love, Jekyll Frogmen, Jersey Sassy, Liaisons Sweet, Lucky Flying, Maguire Apache, Mallrats United, Mask Peach, Roof Champion, Rushmore Mermaid, Smile Earring, Wardrobe Phantom.
```sql
SELECT title FROM actor
	JOIN film_actor
		ON film_actor.actor_id = actor.actor_id
	JOIN film
		ON film_actor.film_id = film.film_id
	WHERE first_name = 'Nick' AND
		last_name = 'Wahlberg';
```
![](https://i.imgur.com/vL9l3de.png)

---
# 고급 SQL 명령어
- timestamps 와 EXTRACT 함수
- Math 함수
- String 함수
- Sub-query 서브쿼리
- Self-join

# Timestamps 와 EXTRACT 함수
## PostgreSQL에서 제공하는 날짜와 시간 정보
- TIME : 시간만 저장(시,분,초)
- DATE : 날짜만 저장(연,월,일,요일)
- TIMESTAMP : 날짜와 시간 저장
- TIMESTAMPZ : 날짜 시간과 + TIMEZONE 저장
## 

![[SQL_TIMESTAMP]]

---
# 평가시험
## 1. How can you retrieve all the information from the cd.facilities table?
- 정답
```sql
SELECT * FROM cd.facilities;
```
![](https://i.imgur.com/XHGTyAb.png)

## 2. You want to print out a list of all of the facilities and their cost to members. How would you retrieve a list of only facility names and costs?
- 정답
```sql
SELECT name, membercost FROM cd.facilities;
```
![](https://i.imgur.com/Wd5TLEL.png)

## 3. How can you produce a list of facilities that charge a fee to members?
- 정답
```sql
SELECT * FROM cd.facilities
	WHERE membercost > 0;
```
![](https://i.imgur.com/EUi3IMo.png)

## 4. How can you produce a list of facilities that charge a fee to members, and that fee is less than 1/50th of the monthly maintenance cost? Return the facid, facility name, member cost, and monthly maintenance of the facilities in question.
- 정답
```sql
SELECT facid, name, membercost, monthlymaintenance
	FROM cd.facilities
	WHERE membercost 
		BETWEEN 1 AND monthlymaintenance/50;
```
![](https://i.imgur.com/Qgha9Ak.png)

## 5. How can you produce a list of all facilities with the word 'Tennis' in their name?
- 정답
```sql
SELECT *
	FROM cd.facilities
	WHERE name LIKE '%Tennis%';
```
![](https://i.imgur.com/g4ioAXG.png)

## 6. How can you retrieve the details of facilities with ID 1 and 5? Try to do it without using the OR operator.
- 정답
```sql
SELECT *
	FROM cd.facilities
	WHERE facid = 1 OR facid = 5;
```
![](https://i.imgur.com/rxTKj1g.png)

## 7. How can you produce a list of members who joined after the start of September 2012? Return the memid, surname, firstname, and joindate of the members in question.
- 정답
```sql
SELECT memid, surname, firstname, joindate
	FROM cd.members
	WHERE joindate >= '2012-09-01';
```
![](https://i.imgur.com/PEU4l3r.png)

## 8. How can you produce an ordered list of the first 10 surnames in the members table? The list must not contain duplicates.
- 정답
```sql
SELECT DISTINCT surname
	FROM cd.members
	ORDER BY surname
	LIMIT 10;
```

## 9. You'd like to get the signup date of your last member. How can you retrieve this information?
- 정답
```sql
SELECT MAX(joindate) AS latest_signup 
	FROM cd.members;
```


## 10. Produce a count of the number of facilities that have a cost to guests of 10 or more.
- 정답
```sql
SELECT COUNT(*) 
	FROM cd.facilities 
	WHERE guestcost >= 10;
```



## 11. Produce a list of the total number of slots booked per facility in the month of September 2012. Produce an output table consisting of facility id and slots, sorted by the number of slots.
- 정답
```sql
SELECT facid, sum(slots) AS "Total Slots" 
	FROM cd.bookings 
	WHERE starttime >= '2012-09-01' AND starttime < '2012-10-01' 
	GROUP BY facid 
	ORDER BY SUM(slots);
```

## 12. Produce a list of facilities with more than 1000 slots booked. Produce an output table consisting of facility id and total slots, sorted by facility id.
- 정답
```sql
SELECT facid, sum(slots) AS total_slots 
	FROM cd.bookings 
	GROUP BY facid 
		HAVING SUM(slots) > 1000 
	ORDER BY facid;
```

## 13. How can you produce a list of the start times for bookings for tennis courts, for the date '2012-09-21'? Return a list of start time and facility name pairings, ordered by the time.
- 정답
```sql
SELECT 
	  cd.bookings.starttime AS start, 
	  cd.facilities.name AS name 
	FROM cd.facilities 
	INNER JOIN cd.bookings
		ON cd.facilities.facid = cd.bookings.facid 
	WHERE cd.facilities.facid IN (0,1) 
		AND cd.bookings.starttime >= '2012-09-21' 
		AND cd.bookings.starttime < '2012-09-22' 
	ORDER BY cd.bookings.starttime;

```

## 14. How can you produce a list of the start times for bookings by members named 'David Farrell'?
- 정답
```sql
SELECT cd.bookings.starttime 
	FROM cd.bookings 
	INNER JOIN cd.members
	ON cd.members.memid = cd.bookings.memid 
	WHERE cd.members.firstname='David' 
	AND cd.members.surname='Farrell';
```


---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 
	
본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다.