
오늘 수강한 강의 : [ 【한글자막】 100일 코딩 챌린지 - Web Development 부트캠프](https://www.udemy.com/course/100-2022-web-development/?utm_source=adwords&utm_medium=udemyads&utm_campaign=WebDevelopment_Search_la.KR_cc.KR&utm_term=_._ag_153638105748_._ad_644611295653_._kw__._de_c_._dm__._pl__._ti_dsa-1939216851836_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA-P-rBhBEEiwAQEXhH8I5AFNq9-SbeYPmP5uwMpj7SzsS-tWDZ-KBEI9inPiFi4XJTAO19hoCjtEQAvD_BwE)

---
# 오늘의 강의 정리 📗
# ==멋있는 웹사이트 만들기==
## [CSS 변수](https://developer.mozilla.org/ko/docs/Web/CSS/Using_CSS_custom_properties)
### 변수의 선언 : "--"로 시작하는 변수명 : 사용하고자 하는 속성
- 일반 속성과 마찬가지로 요소 내부에 선언하면 되나, 보통은 root 의사선택자 안에 적용해서 전역으로 사용
```
main {
	--main-bg-color : brown;
}
:root {
	--main-ft-color: rgb(255,255,255);
}
```
### 변수 사용 : var("CSS 변수명", [해당 변수가 없을시 사용할 속성])
```
main {
	background-color: var(--main-bg-color)
}
```
### CSS 변수의 상속
- 상위 엘리먼트의 변수값은 하위 엘리먼트로 상속됨
- 하위 엘리먼트에 선언된 변수값은 상위 엘리먼트에서는 사용 불가능

## CSS 전역 변수 : ":root", "html", "body"선택자 사용해 변수 정의

## CSS transition : CSS 프로퍼티의 값이 변화할 때, 프로퍼티 값의 변화가 일정 시간(duration)에 걸쳐 일어나도록 하는 것
- 구성요소
```
선택자 { 
	transition-property: width, opacity;
	transition-duration: 2s, 4s; 
	transition-timing-function: ease, liner;
	transition-delay: 0s, 1s;
}

//ShortCut
선택자 {
	transition : property duration timing-function dlay
}
```
![](https://i.imgur.com/T9c3HYE.png)
- property : 트랜지션의 대상이 되는 CSS 프로퍼티를 지정
```
/* 프로퍼티 종류 */
// Box model 
width height max-width max-height min-width min-height padding margin border-color border-width border-spacing 
// Background 
background-color background-position 
// 좌표 
top left right bottom 
// 텍스트 
color font-size font-weight letter-spacing line-height text-indent text-shadow vertical-align word-spacing 
// 기타 
opacity outline-color outline-offset outline-width visibility z-index
```
	- cf) 레이아웃에 영향을 주는 트랜지션 효과는 가능한 피해야 함
- duration :  트랜지션에 일어나는 지속시간(duration)을 초 단위(s) 또는 밀리 초 단위(ms)로 지정
	-  프로퍼티값을 지정하지 않을 경우 기본값 0s이 적용되어 어떠한 트랜지션 효과도 볼 수 없음
- timing function : 트랜지션 효과의 변화 흐름, 시간에 따른 변화 속도와 같은 일종의 변화의 리듬을 지정

|프로퍼티값|효과|그래프|
|---|---|---|
|ease|기본값. 느리게 시작하여 점점 빨라졌다가 느리지면서 종료한다.|![](https://poiemaweb.com/img/cubic-bezier-ease.png)|
|linear|시작부터 종료까지 등속 운동을 한다.|![](https://poiemaweb.com/img/cubic-bezier-linear.png)|
|ease-in|느리게 시작한 후 일정한 속도에 다다르면 그 상태로 등속 운동한다.|![](https://poiemaweb.com/img/cubic-bezier-ease-in.png)|
|ease-out|일정한 속도의 등속으로 시작해서 점점 느려지면서 종료한다.|![](https://poiemaweb.com/img/cubic-bezier-ease-out.png)|
|ease-in-out|ease와 비슷하게 느리게 시작하여 느리지면서 종료한다.|![](https://poiemaweb.com/img/cubic-bezier-ease-in-out.png)|
- delay : 프로퍼티의 값이 변화하여도 즉시 트랜지션이 실행되지 않고, 일정 시간 대기한 후 트랜지션이 실행되도록 지정

## SVG(Scalable Vector Graphics) : 2차원 벡터 그래픽을 서술하는 XML 기반의 마크업 언어
- 장점 : 
	- 웹사이트 로딩 속도가 빠름
	- 어떤 크기에서든 재활용이 가능(Future Proof)
	- SEO 친화적
	- CSS로 디자인 수정이 가능
- 단점 : 너무 복잡한 SVG의 경우엔 비효율적일 수 있음. 

# ==웹사이트에 양식 추가==
## HTML [FORM](https://developer.mozilla.org/ko/docs/Web/HTML/Element/form) 요소

![](https://i.imgur.com/BVl0upH.png)



---
# 오늘의 멘토링 🥸
- Q1 : `[Y군]` ‘백엔드 개발자 포지션을 맡고 있더라도, 어드민 페이지 정도는 스스로 만들 수 있는 수준의 프론트 엔드 개발 능력을 갖춰야 한다’ 라고 알고 있다
	- A : 정확히 말하면 "하면 좋다"이다. 
- Q2 : `[YANA]`현재 애자일 스크럼 방식으로 지라를 활용중에있으며, 스크럼 마스터의 경우엔 팀원들이 스프린트마다 돌아가면서 맡기러 했는데, 스크럼 마스터의 역할이 어디부터 어디까지일지 궁금해 문의 드립니다..!
  그리고 스크럼 마스터를 팀원들이 돌아가면서 맡는것이 관련 맞는 선택일지, 현업에서는 보통 어떤 사람이 스크럼 마스터를 맡는지 궁금합니다!
	- A : 정하기 나름. 모든 그 날의 기록을 책임짐. PR 리뷰 독촉을 맡음. 누군가 blocking point가 되는것을 찾는 역할을 함. 계속 진행되지 않는 일에 대해서는 push 하는 역할을 함. 하기러 한것을 체크한다.
	  돌아가면서 맡는게 맞다고 본다. 그 역할을 맡지 않아본 경우에는 이해를 하기 어려웠던 것이, 맡아보고나면 이해가 되기 때문이다. 초반에는 모든걸 아는 사람이 일주일정도 맡아야한다.
- Q3 : `[YANA]`현업에서 **commit message의 body**에 상세한 내용을 적는 경우가 많은지 궁금하면서, 현업에서는 **PR merge** 시에는 보통 **어떤 merge 전략**을 주로 가져가시는지 궁금합니다..!
	- A : 설명이 필요한 commit은 지양하는것이 좋다.
	  장애가 나거나, 버그가 발생한 경우 '언제 merge 된지가 가장 중요하다.' 해당 인식의 경우에는 일반 merge가 유리하다. 
- Q4 : 알고리즘 문제를 풀때 테스트 케이스 작성 요령이 궁금합니다.
	- A : 인계값을 확인한다. 입력값 범위 검사를 얼마나 세심하게 했는지 중요하다. 중복값이 있을 때를 테스트 해본다던가 하는 방식이 있을 것 같다.

---
# 오늘의 팀스터디 🥊
# 정렬
## 버블 정렬(Bubble Sort) - 시 **O(n^2)** | 공 **O(n)**
###     서로 인접한 두 원소의 대소를 비교, 조건이 맞지 않다면 자리를 교환해 정렬
- 선택정렬(Selection Sort)과 유사
- 배열의 길이가 길어질수록 비효율적
- 시간 복잡도 계산
	- (n-1) + (n-2) + (n-3) + .... + 2 + 1 => n(n-1)/2
	- 최선, 평균, 최악의 경우 모두 시간복잡도가 **O(n^2)** 으로 동일
- 공간 복잡도 : O(n)

![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/bubble-sort-001.gif)
```
void bubbleSort(int[] arr) {
    int temp = 0;
	for(int i = 0; i < arr.length; i++) {       // 1.
		for(int j= 1 ; j < arr.length-i; j++) { // 2.
			if(arr[j-1] > arr[j]) {             // 3.
                // swap(arr[j-1], arr[j])
				temp = arr[j-1];
				arr[j-1] = arr[j];
				arr[j] = temp;
			}
		}
	}
	System.out.println(Arrays.toString(arr));
}
```

## 선택 정렬(Selection Sort) - 시 **O(n^2)** | 공 **O(n)**
###     해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘
- 버블 정렬과 유사하지만 조금 더 빠름.
	- 정렬을 위한 비교 횟수는 많음.
	- Bubble Sort에 비해 실제로 교환하는 횟수는 적기 때문에 많은 교환이 일어나야 하는 자료상태에서 비교적 효율적임.
- 배열의 길이가 길어질수록 비효율적
- 시간 복잡도 계산
	- (n-1) + (n-2) + .... + 2 + 1 => n(n-1)/2
	- 최선, 평균, 최악의 경우 시간복잡도는 **O(n^2)**
- 공간 복잡도 : O(n)

![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/selection-sort-001.gif)
```
void selectionSort(int[] arr) {
    int indexMin, temp;
    for (int i = 0; i < arr.length-1; i++) {        // 1.
        indexMin = i;
        for (int j = i + 1; j < arr.length; j++) {  // 2.
            if (arr[j] < arr[indexMin]) {           // 3.
                indexMin = j;
            }
        }
        // 4. swap(arr[indexMin], arr[i])
        temp = arr[indexMin];
        arr[indexMin] = arr[i];
        arr[i] = temp;
  }
  System.out.println(Arrays.toString(arr));
}
```

## 삽입 정렬(Insertion Sort) - 시 O(N)~**O(n^2)** | 공 **O(n)**
###     2번째 원소부터 시작하여 그 앞(왼쪽)의 원소들과 비교하여 삽입할 위치를 지정한 후, 원소를 뒤로 옮기고 지정된 자리에 자료를 삽입
- 선택 정렬과 유사하지만, 조금 더 효율적임
- 배열의 길이가 길어질수록 비효율적
- 시간 복잡도 계산
	- (n-1) + (n-2) + .... + 2 + 1 => n(n-1)/2
	- 최선 -  **O(n)** , 평균&최악 -  **O(n^2)**
- 공간 복잡도 : O(n)

![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/insertion-sort-001.gif)
```
void insertionSort(int[] arr)
{
   for(int index = 1 ; index < arr.length ; index++){ // 1.
      int temp = arr[index];
      int prev = index - 1;
      while( (prev >= 0) && (arr[prev] > temp) ) {    // 2.
         arr[prev+1] = arr[prev];
         prev--;
      }
      arr[prev + 1] = temp;                           // 3.
   }
   System.out.println(Arrays.toString(arr));
}
```

## 퀵 정렬(Quick Sort) - 시 **O(nlog₂n)**~ **O(n^2)** | 공 **O(n)**
###     분할 정복(divide and conquer) 방법 을 통해 주어진 배열을 정렬(JAVA Arrays.sort() : 퀵 정렬 알고리즘)
	`*`[분할 정복(divide and conquer) 방법]
	문제를 작은 2개의 문제로 분리하고 각각을 해결한 다음, 결과를 모아서 원래의 문제를 해결하는 전략
- 빠른정렬로 분류되며, 병합 정렬과 함께 많이 언급됨
- 정렬하고자 하는 배열이 오름차순 정렬되어있거나 내림차순 정렬되어있으면 O(n^2)의 시간복잡도를 가짐(수행시간이 매우 길어짐)
- 불필요한 데이터의 이동을 줄이고 먼 거리의 데이터를 교환할 뿐만 아니라, 한 번 결정된 피벗들이 추후 연산에서 제외됨
	- 다른 정렬 알고리즘과 비교했을 때도 가장 빠름
- 시간 복잡도 계산
	- 순환 호출의 깊이 * 각 순환 호출 단계의 비교 연산
	- 최선 : log₂n * n = nlog₂n  / 최악 : n * n = n^2
- 공간 복잡도 : O(n)

![](https://i.imgur.com/RCFgNwK.png)
![](https://i.imgur.com/uydN4S1.png)
![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/quick-sort-001.gif)
1. 정복(conquer)
```
public void quickSort(int[] array, int left, int right) {
    if(left >= right) return;
    
    // 분할 
    int pivot = partition(); 
    
    // 피벗은 제외한 2개의 부분 배열을 대상으로 순환 호출
    quickSort(array, left, pivot-1);  // 정복(Conquer)
    quickSort(array, pivot+1, right); // 정복(Conquer)
}
```
2. 분할(Divide)
```
public int partition(int[] array, int left, int right) {
    /**
    // 최악의 경우, 개선 방법
    int mid = (left + right) / 2;
    swap(array, left, mid);
    */
    
    int pivot = array[left]; // 가장 왼쪽값을 피벗으로 설정
    int i = left, j = right;
    
    while(i < j) {
        while(pivot < array[j]) {
            j--;
        }
        while(i < j && pivot >= array[i]){
            i++;
        }
        swap(array, i, j);
    }
    array[left] = array[i];
    array[i] = pivot;
    
    return i;
}
```
## 병합(합병) 정렬(Merge Sort) - 시 Ω(nlogn) ~ Θ(nlogn)	~ O(nlogn) | 공 O(1)
###     요소를 쪼갠 후, 다시 합병시키면서 정렬해나가는 방식
- 분할 정복 방법으로 구현
- 빠른정렬로 분류되며, 퀵 정렬과 함께 많이 언급됨
- 퀵정렬과의 차이점
	- 퀵정렬 : 우선 피벗을 통해 정렬(partition) → 영역을 쪼갬(quickSort)
	- 합병정렬 : 영역을 쪼갤 수 있을 만큼 쪼갬(mergeSort) → 정렬(merge)
- 합병의 대상이 되는 두 영역이 각 영역에 대해서 정렬이 되어있기 때문에, 단순히 두 배열을 순차적으로 비교하면서 정렬할 수가 있음
- LinkedList를 퀵정렬을 통해 정렬하면 성능이 좋지 않음 -> **병합정렬 사용**
	- 퀵정렬의 경우, 순차 접근이 아닌 임의 접근이기 때문
	- 따라서, 오버헤드 발생이 증가하게 됨

![](https://cdn-images-1.medium.com/max/1600/1*Uvs7CK1oew0pVckcuxr_qA.gif)
1. mergeSort
```
public void mergeSort(int[] array, int left, int right) {
    
    if(left < right) {
        int mid = (left + right) / 2;
        
        mergeSort(array, left, mid);
        mergeSort(array, mid+1, right);
        merge(array, left, mid, right);
    }
    
}
```
2. merge()
```
public static void merge(int[] array, int left, int mid, int right) {
    int[] L = Arrays.copyOfRange(array, left, mid + 1);
    int[] R = Arrays.copyOfRange(array, mid + 1, right + 1);
    
    int i = 0, j = 0, k = left;
    int ll = L.length, rl = R.length;
    
    while(i < ll && j < rl) {
        if(L[i] <= R[j]) {
            array[k] = L[i++];
        }
        else {
            array[k] = R[j++];
        }
        k++;
    }
    
    // remain
    while(i < ll) {
        array[k++] = L[i++];
    }
    while(j < rl) {
        array[k++] = R[j++];
    }
}
```
## 힙 정렬(Heap Sort)

## 기수 정렬(Radix Sort)

## 계수 정렬(Counting Sort)



---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 
유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프