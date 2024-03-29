---
tistoryBlogName: yanacoding
tistoryTitle: "[DB] Index란?"
tistoryVisibility: "3"
tistoryCategory: "1155358"
tistorySkipModal: true
tistoryPostId: "258"
tistoryPostUrl: https://yanacoding.tistory.com/258
---
소유자: 야나

인증: 인증 완료

Main Category: CS

Category: DB

Status.: In progress

Tags: DB, NoSQL, RDB, RDBMS

생성 일시: 2023년 5월 22일 오후 3:31

생성자: 야나

최종 편집자: 야나

  

# Index



---

  

## Index란?

  

<aside>

📌 사전 : 색인, 지표, 기호 또는 무언가의 척도

  

DB관점 : 추가적인 쓰기 작업과 저장 공간을 활용하여 데이터베이스 테이블의 검색 속도를 향상시키기 위한 자료구조. 데이터베이스 안의 레코드를 처음부터 풀스캔하지 않고, B+ Tree로 구성된 구조에서 Index 파일 검색으로 속도를 향상시키는 기술이다.

  

테이블의 칼럼을 색인화한다. 마치, 두꺼운 책의 목차와 같다고 생각하면 편함.

  

</aside>

  

인덱스는 항상 최신의 정렬 상태를 유지한다.

  

인덱스도 하나의 데이터베이스 객체이다

  

따라서, 데이터베이스 크기의 약 10%정도의 저장공간을 필요로 한다

  

페이지 : 데이터가 저장되는 단위(ex mySQL : 16Kbyte)

  

Full Table Scan : 순차적으로 처음부터 끝까지 모든 데이터를 탐색. 접근비용이 감소

  

적용 가능한 인덱스가 없는 경우

  

인덱스 처리 범위가 넚은 경우

  

크기가 작은 테이블에 접근하는 경우

  

SELECT 의 경우 성능 향상 Good, but INSERT, UPDATE, DELETE?

  

INSERT : 페이지의 규모보다 데이터가 더 많아진 경우 빈 테이블 생성 후 분할저장

  

페이지 분할 : 페이지에 새로운 데이터를 추가할 공간이 없어 발생.

  

ㄴ→ DB가 느려지고 성능에 영향을 줌

  ![](https://i.imgur.com/HWJwogk.png)


  

DELETE : 지우지 않고 사용 안함 표시

  

UPDATE : DELETE를 통해 기존값을 사용안함 표시 후 변경된 값 삽입

  

결론 : 조회성능은 향상되지만, INSERT, UPDATE, DELETE에서는 사용하지 않는 인덱스가 적용되었다면 불필요한 처리량이 증가하며, 사용안함 표시로 인해 페이지 낭비 및 인덱스 조각화가 심해짐

  

- 인덱스는 왜 사용하는 것인가요?

    - 데이터베이스 테이블에 대한 검색 성능을 향상시키는 자료 구조이며, where절 등을 통해 활용된다.

- 인덱스는 크게 Hash 인덱스와 B-Tree 인덱스가 있습니다. 어떠한 차이가 있을까요?

    - B - tree

        - 항상 정렬된 상태를 유지한다. 따라서 삽입과 삭제시에도 정렬이 발생

        - 일반적인 DBMS에서 기본으로 사용

    - Hash index

        - 정렬되어있다고 볼 수 없다

        - 해싱된 데이터 값에 까라 저장될 버킷의 위치를 정하기에, 빠른속도로 검색 영역을 제한 할 수 있음

        - 정렬 할 필요 없어 삽입, 삭제가 빠름

        - Mysql  innoDB 에는 메모리 버퍼 풀에서 레코드 검색을 위한 어댑티브 해시 인덱스로 사용(`Innodb_Buffer_Pool_Size`의 `1/64`)

- B-Tree 인덱스와 B+-Tree 인덱스의 차이는 무엇인가요?

    - B - tree : 이진 탐색(Binary Search Tree) 모든 노드가 여러 키를 포함하고 2개 이상의 자식을 갖는 자체 균형 탐색 트리. 기본 DB Index 구조

        - 균형있는 이진탐색트리 시간복잡도 : O(log n)

        - 균형없는 이진탐색트리 시간복잡도 : O(n)

            - 따라서 이진탐색트리의 단점을 극복하기위해 노드를 2개씩 가능하게

        - ********************************************트리 높이가 같음********************************************

        - ****자식 노드를 2개 이상 가질 수 있음****

            ![](https://i.imgur.com/fj6tZul.png)


    - B+ - tree : B - tree 에서 리프 페이지의 노드들이 연결리스트로 구현되어있음

        - 범위 탐색시 유리

        - 데이터의 삽입 삭제는 리프노드에서만 발생

- 인덱스 Scan 방식은 무엇이 있나요?

    - ****INDEX RANGE SCAN : 필요한 범위만 스캔****

    - ****INDEX RANGE SCAN DESCENDING: INDEX RANGE SCAN을 역순으로****

    - ****INDEX FULL SCAN : 수직 탐색 없이 리프를 수평적으로 순차탐색****

        - 마땅한 인덱스가 없을때

    - ****INDEX FAST FULL SCAN :****

        - INDEX FULL SCAN보다 빠름

        - INDEX FULL SCAN은 논리적 구조에따라 읽지만, FFS는 물리적으로 디스크에 저장된 순서

    - ****INDEX UNIQUE SCAN : 수직탐색으로만 탐색****

        - 등치(=)조건으로 탐색하는 경우에만 작동

        - UNIQUE INDEX라해도 범위검색조건 (BETWEEN, 부등호, LIKE)로 검색할때는 IDNEX RANGE SCAN으로 처리된다.

    - ****INDEX SKIP SCAN :****

- 좋은 인덱스를 설계하기 위해 고려해야 하는 조건으로는 무엇이 있는지 아시나요?

    - 카디널리티(Cardinality) : 그룹 내 요소의 개수

        - 카디널리티가 높은, 즉 중복율이 낮은 칼럼을 우선적으로 고려해야 함

        - WHERE, JOIN, Order By절에 자주 사용되는 컬럼

            - 조건절이 없다면 인덱스가 사용되지 않기 때문

        - INSERT, UPDATE, DELETE가 자주 일어나지 않는 컬럼

- 인덱스 적용이 어려운 요인에는 무엇이 있을까요?

    - DB 사이즈 증가

    - DML 성능 저하

    - DB관리 및 운영비용 상승

- 인덱스 설계시 NULL값은 고려되야 할까요? 고려해야 한다면 어떤 이유인가요?

    - Null 값이 인덱스가 되어버려 저장공간이 낭비 될 수 있음

    - 데이터베이스 시스템에서 어떻게 처리하는지 확인해서 Null 여부를 처리해줘야 함

- 클러스터 인덱스와 논클러스터 인덱스는 어떤 차이가 있나요?

    - 클러스터링 인덱스 : 실제 데이터와 무리를 이룸

        - ex : 사전의 색인

        - PK적용 / notnull + unique제약조건 설정 :  자동으로 클러스터링 인덱스 적용

        - 실제 데이터 자체가 정렬

    - 논-클러스터링 인덱스 : 실제 제이터와 무리를 이루지 않음

        - ex : 책 목차의 페이지

        - unique적용 / index 또는 unique index 자체 생성시 자동으로 논 클러스터링 인덱스 적용

        - 실제 데이터 페이지는 그대로

        - 별도의 인덱스 페이지 생성(추가공간 필요)

        - 테이블당 여러개 존재 가능

          ![](https://i.imgur.com/Wqf82JC.png)


    - 두 인덱스를 동시에 적용하면?

        - 논클러스터링 데이터의 데이터페이지 주소가 담겨있는게 아닌 클러스터링 인덱스가 담겨있음

        ![](https://i.imgur.com/8B8NtZJ.png)


- 인덱스(Index Server) 샤딩 방식에 대해서 아시나요?

    - 엘라스틱 서치 관련…?

- DB샤딩

    - 수평 분할(Horizontal Partitioning)과 동일하며, 인덱스의 크기를 줄이고, 작업 동시성을 늘리기 위한 것

    - 스키마(schema)가 같은 데이터를 두 개 이상의 테이블에 나누어 저장하는 디자인

    - 분산된 DB에서 어떻게 Data를 읽어올지, 분산된 DB에 데이터를 어떻게 분산시킬지 고민해야함.

    - 단점

        - 프로그래밍적, 운영적인 복잡도가 높아진다

  

## 참고자료


express를 nest하게 짠다는걸 시도해본다
