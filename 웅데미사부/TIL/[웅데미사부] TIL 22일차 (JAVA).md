---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 22일차 (JAVA)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "261"
tistoryPostUrl: https://yanacoding.tistory.com/261
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
## 자바 프로그래밍의 참조형(Reference Type)
참조형의 특징은 다음과 같다.
1. 값이 아닌 자료가 저장된 공간의 ˇ 저장
	- 값은 다른 곳에 있으며, 값은 그 주소를 참조해서 가져올 수 있다.
2. 메모리의 힙(Heap)에 실제 값을 저장 - 그 참조값을 가지는 변수는 스택에 저장
3. 참조형 변수는 null로 초기화 할 수 있다

## 자바 프로그래밍의 [컬렉션](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/index.html)
다수의 데이터를 쉽고 효과적으로 처리 할 수 있는 표준화된 방법을 제공하는 클래스의 집합

컬렉션 프레임 워크는 자바의 Interface를 사용해 구현됨

#### 컬렉션 프레임워크의 주요 인터페이스
List와 Set인터페이스는 공통된 부분이 있어 Collection 인처페이스에서 정의되고있지만, Map의 경우 구조적인 차이로 인해서 별도로 정의됨.
![](https://i.imgur.com/WYlkWc2.png)
##### List Interface
순서가 있는 데이터의 집합 - 데이터의 중복 허용
구현 클래스 : Vector(대체 -> ArrayList), ArrayList, LinkedList, Stack, Queue
##### Set Interface
순서가 없는 데이터의 집합 - 데이터의 중복을 허용하지 
구현 클래스 : HashSet, TreeSet
##### Map Interface
키와 값이라는 한 쌍으로 이루어지는 데이터 집합 - 순서가 없음.(키 : 중복 x , 값 : 중복 o)
구현 클래스 : HashMap, TreeMap, Hashtable(대체 -> HashMap), Properties
#### collection class
컬렉션 프레임워크에 속하는 인터페이스를 구현한 클래스.
List, Set, Map 인터페이스 중 하나의 인터페이스를 구현하고있음.
#### collection Interface
|메소드|설명|
|---|---|
|boolean add(E e)|해당 컬렉션(collection)에 전달된 요소를 추가함. (선택적 기능)|
|void clear()|해당 컬렉션의 모든 요소를 제거함. (선택적 기능)|
|boolean contains(Object o)|해당 컬렉션이 전달된 객체를 포함하고 있는지를 확인함.|
|boolean equals(Object o)|해당 컬렉션과 전달된 객체가 같은지를 확인함.|
|boolean isEmpty()|해당 컬렉션이 비어있는지를 확인함.|
|Iterator<E> iterator()|해당 컬렉션의 반복자(iterator)를 반환함.|
|boolean remove(Object o)|해당 컬렉션에서 전달된 객체를 제거함. (선택적 기능)|
|int size()|해당 컬렉션의 요소의 총 개수를 반환함.|
|Object[] toArray()|해당 컬렉션의 모든 요소를 Object 타입의 배열로 반환함.|
#### [자바의 Stream API](https://yanacoding.tistory.com/entry/JAVA-Stream-API)
---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 