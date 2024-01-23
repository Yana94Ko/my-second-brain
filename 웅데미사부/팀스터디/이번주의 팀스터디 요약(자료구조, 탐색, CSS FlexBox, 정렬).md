---
tistoryBlogName: yanacoding
tistoryTitle: 이번주의 팀스터디 요약(자료구조, 탐색, CSS FlexBox, 정렬)
tistoryVisibility: "3"
tistoryCategory: "1205801"
tistoryPostId: "222"
tistoryPostUrl: https://yanacoding.tistory.com/222
tistorySkipModal: true
---
# 미친피자먹어조의 팀스터디 🥊
# 월요일 : 스택 큐 BFS DFS 개인 공부 | 화요일 : 발표
![](https://i.imgur.com/oKvoGOm.png)

![](https://i.imgur.com/7s6yHUw.png)






![](https://i.imgur.com/WmJzH5c.png)


# BFS & DFS

![](https://i.imgur.com/XQkZvWh.gif)

---
# 수요일 : CSS - Flex Bok 스터디([게임](https://flexboxfroggy.com/#ko))

![](https://i.imgur.com/jBu4TWw.png)

---
# 목요일 : 정렬 개인공부 | 금요일 : 정렬 발표
## 버블 정렬(Bubble Sort) - 시 **O(n^2)** | 공 **O(n)**
###     서로 인접한 두 원소의 대소를 비교, 조건이 맞지 않다면 자리를 교환해 정렬

![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/bubble-sort-001.gif)

## 선택 정렬(Selection Sort) - 시 **O(n^2)** | 공 **O(n)**
###     해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘
![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/selection-sort-001.gif)

## 삽입 정렬(Insertion Sort) - 시 O(N)~**O(n^2)** | 공 **O(n)**
###     2번째 원소부터 시작하여 그 앞(왼쪽)의 원소들과 비교하여 삽입할 위치를 지정한 후, 원소를 뒤로 옮기고 지정된 자리에 자료를 삽입

![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/insertion-sort-001.gif)

## 퀵 정렬(Quick Sort) - 시 **O(nlog₂n)**~ **O(n^2)** | 공 **O(n)**
###     분할 정복(divide and conquer) 방법 을 통해 주어진 배열을 정렬(JAVA Arrays.sort() : 퀵 정렬 알고리즘)
![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/quick-sort-001.gif)

## 병합(합병) 정렬(Merge Sort) - 시  O(nlogn) | 공 O(1)
###     요소를 쪼갠 후, 다시 합병시키면서 정렬해나가는 방식

![](https://cdn-images-1.medium.com/max/1600/1*Uvs7CK1oew0pVckcuxr_qA.gif)

## 힙 정렬(Heap Sort) - 시 O(nlogn) | 
###     완전 이진 트리를 기본으로 하는 힙(Heap) 자료구조를 기반으로 한 정렬 방식
`*` 완전 이진 트리 : 삽입 할 때 왼쪽부터 차례대로 추가하는 이진 트리

![](https://upload.wikimedia.org/wikipedia/commons/4/4d/Heapsort-example.gif)

## 기수 정렬(Radix Sort) - 시  O(w * (k+n)) | 
###     기수별로 비교 없이 수행하는 정렬 알고리즘

![](https://blog.kakaocdn.net/dn/ddDUGV/btqEADkQR6A/z1wVWgKYukaCuQGFTwaKq1/img.gif)

## 계수 정렬(Counting Sort)
- 정렬 과정
	1. 가장 작은 데이터부터 가장 큰 데이터까지의 범위가 모두 담길 수 있는 리스트를 생성
	2. 데이터를 하나씩 확인하며 데이터의 값과 동일한 인덱스의 데이터를 1씩 증가
	3. 증가된 리스트에서 0인 값을 제외하고, 인덱스를 인덱스 값만큼 출력

![](https://d18l82el6cdm1i.cloudfront.net/uploads/hrUDdYC7OH-countingsort.gif)


# Q : 
## 0~9사이의 숫자 10,000개를 정렬 할 때와 
## 0~20,000사이의 숫자 10,000개를 정렬 할 때
각각 기수정렬과 개수 정렬을 사용한다면... 각각의 경우에 어떤 정렬이 유리할 까요?
---
# 회고
 - 야나 : 자료구조와 알고리즘 기초부터, CSS 강의내용을 재밌게 복습 할 수 있던 게임까지 알차게 한 주 팀스터디 진행 한 것 같아서 좋았습니다 :) 개인적으로는 정렬에 대해서 조금 더 제대로 복습하고 정리해야 할 것 같다고 느꼈어요. 💻
 - 효은 : 평소 정렬에 대해 한번 제대로 정리해보고 싶었는데, 이번 기회에 확실히 공부하게 된 것 같아 뜻깊은 시간이였습니다. Flexbox도 재밌는 게임으로 공부하니 재밌었어요 🐸
 - 준영 : 배경지식이 없어 다 생소한 내용이었는데, 모든 것을 이해하지는 못했지만 새로운 지식을 머리에 채워간다는 충족감과 아직 갈 길이 멀었다는 아득함이 공존했습니다.
 - 지명 : 새롭게 알게 된, 다시 상기하게 된 알고리즘도 있고 공부한 내용을 팀원들에게 설명한 과정에서 지식이 더 단단해진 느낌입니다 ㅎㅎ