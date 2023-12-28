---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 5일차 (HTML CSS 레이아웃 및 포지셔닝, 반응형 이해하기)"
tistoryTags: 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistoryPostId: "218"
tistoryPostUrl: https://yanacoding.tistory.com/218
tistorySkipModal: true
---
오늘 수강한 강의 : [ 【한글자막】 100일 코딩 챌린지 - Web Development 부트캠프](https://www.udemy.com/course/100-2022-web-development/?utm_source=adwords&utm_medium=udemyads&utm_campaign=WebDevelopment_Search_la.KR_cc.KR&utm_term=_._ag_153638105748_._ad_644611295653_._kw__._de_c_._dm__._pl__._ti_dsa-1939216851836_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA-P-rBhBEEiwAQEXhH8I5AFNq9-SbeYPmP5uwMpj7SzsS-tWDZ-KBEI9inPiFi4XJTAO19hoCjtEQAvD_BwE)

# 오늘의 강의 정리 📗
<목차여기>
## ==HTML CSS 레이아웃 및 포지셔닝==
### text 스타일링
### margin 축소(중복)
- 인접 요소끼리만 margin 축소 현상이 일어나는게 아니라, 부모자식 요소 사이에서도 margin 축소가 일어남.

### 선형 그라디언트
```
linear-gradient( to right, yellow 50%, red 60%, purple )
```

### [position](https://developer.mozilla.org/ko/docs/Web/CSS/position)
- static : (default) 요소를 일반적인 문서 흐름에 따라 배치
	![](https://res.cloudinary.com/practicaldev/image/fetch/s--FaNHLalq--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/10jv0ntujnawitbqahyg.gif)
	- 차례대로 왼쪽에서 오른쪽, 위에서 아래로 쌓임

- relative : 요소를 일반적인 문서 흐름에 따라 배치하고, 자기 자신을 기준으로 `top`, `right`, `bottom`, `left`의 값에 따라 오프셋 적용
	![](https://res.cloudinary.com/practicaldev/image/fetch/s--SNFAC7hG--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/q6dw4wvpu5gzg9cjfkmp.gif)

- absolute : 가장 가까운 위치 지정 조상 요소에 대해 상대적으로 배치
	![](https://res.cloudinary.com/practicaldev/image/fetch/s--fIjJaDhp--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/7q69pj4rsrjyrvuwtoez.gif)
	- 요소를 일반적인 문서 흐름에서 제거하고, 페이지 레이아웃에 공간도 배정하지 않음.

- fixed :  [뷰포트](https://developer.mozilla.org/ko/docs/Glossary/Viewport)의 초기 [컨테이닝 블록](https://developer.mozilla.org/ko/docs/Web/CSS/Containing_block)을 기준으로 삼아 배치
	![](https://res.cloudinary.com/practicaldev/image/fetch/s--vBCbFH6c--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/34sudmm11w2yn8q5m710.gif)
	- 요소를 일반적인 문서 흐름에서 제거하고, 페이지 레이아웃에 공간도 배정하지 않음.
	- 단, 요소의 **조상 중 하나가 `transform`, `perspective`, `filter` 속성 중 어느 하나라도 `none`이 아니라면** ([CSS Transforms 명세](https://www.w3.org/TR/css-transforms-1/#propdef-transform) 참조) 뷰포트 대신 그 조상을 컨테이닝 블록으로 삼음.

- sticky : 요소를 일반적인 문서 흐름에 따라 배치하고, 테이블 관련 요소를 포함해 가장 가까운, 스크롤 되는 조상과, 표 관련 요소를 포함한 [컨테이닝 블록](https://developer.mozilla.org/ko/docs/Web/CSS/Containing_block)(가장 가까운 블록 레벨 조상) 을 기준으로 `top`, `right`, `bottom`, `left`의 값에 따라 오프셋을 적용.

---
### ==grid : 양방향 레이아웃 시스템(2차원)==
- flex : 한방향 레이아웃 시스템(1차원)

## display: grid
- 그리드 설정의 시작
```
.container { 
	display: grid; 
}
```

## gird 용어
![](https://i.imgur.com/FavhtYE.png)
## Grid Container(그리드 컨테이너)
- 부모요소
- Grid의 영향을 받는 전체 공간
## Grid Item(그리드 아이템)
- 자식요소
- 컨테이너 내부의 각각의 아이템들이 설정된 속성에 따른 형태로 배치
## 그리드 트랙 (Grid Track)
- Grid의 행(Row) 또는 열(Column)
## 그리드 셀 (Grid Cell)
- Grid의 한 칸
- 즉, `<div>`처럼 실제 html 요소인 Grid 아이템 하나가 들어가는 “가상의 칸(틀)”
## 그리드 라인(Grid Line)
- Grid 셀을 구분하는 선
## 그리드 번호(Grid Number)
- Grid 라인의 각 번호
## 그리드 갭(Grid Gap)
- Grid 셀 사이의 간격
## 그리드 영역(Grid Area)
- Grid 라인으로 둘러싸인 사각형 영역. 
- 즉, 그리드 셀의 집합

## Grid 컨테이너에 적용하는 속성
### display : gird / inline-grid
- inline-grid : 컨테이너가 주변 요소들과 어떻게 어우러질지 결정(Like inline-block)

### grid-template-rows, grid-template-columns
- Grid 트랙의 크기들을 지정해주는 속성
	- grid-template-rows : 행(row)의 배치
	- grid-template-columns : 열(columns)의 배치
```
.container { 
	grid-template-columns: 200px 200px 500px; 
	/* grid-template-columns: 1fr 1fr 1fr */ 
	/* grid-template-columns: repeat(3, 1fr) */ 
	/* grid-template-columns: 200px 1fr */ 
	/* grid-template-columns: 100px 200px auto */ 
	grid-template-rows: 200px 200px 500px; 
	/* grid-template-rows: 1fr 1fr 1fr */ 
	/* grid-template-rows: repeat(3, 1fr) */ 
	/* grid-template-rows: 200px 1fr */ 
	/* grid-template-rows: 100px 200px auto */ 
}
```
### repeat 함수 : 반복되는 값을 자동으로 처리할 수 있는 함수
- repeat(반복횟수, 반복값)
```
.container { 
	grid-template-columns: repeat(5, 1fr); 
	/* grid-template-columns: 1fr 1fr 1fr 1fr 1fr */ 
}
```

### minmax 함수 : 최솟값과 최댓값을 지정할 수 있는 함수
- minmax(최솟값, 최댓값)
```
.container { 
	grid-template-columns: repeat(3, 1fr); 
	grid-template-rows: repeat(3, 
	minmax(100px, auto)); 
}
```

### auto-fill, auto-fit : column의 개수를 미리 정하지 않고 설정된 너비가 허용하는 한 최대한 셀을 채움

### row-gap , column-gap , gap : 간격 설정
```
.container { 
	row-gap: 10px; /* row의 간격을 10px로 */ 
	column-gap: 20px; /* column의 간격을 20px로 */ 
}
```

```
.container { 
	gap: 10px 20px; /* row-gap: 10px; column-gap: 20px; */ 
}
.container { 
	gap: 20px; /* row-gap: 20px; column-gap: 20px; */ 
}
```

### grid-auto-columns , grid-auto-rows : 그리드 형태 자동 지정

## Grid 아이템에 적용하는 속성
### 각 셀 영역 지정
- grid-column-start  
- grid-column-end  
- grid-column  
- grid-row-start  
- grid-row-end  
- grid-row

![](https://i.imgur.com/3YDlJNg.png)


![](https://i.imgur.com/PRF0TAM.png)

```
.item:nth-child(1) { 
	grid-column-start: 1; 
	grid-column-end: 3; 
	grid-row-start: 1; 
	grid-row-end: 2; 
}

/*위 아래 스타일링은 동일한 효과를 냄*/

.item:nth-child(1) { 
	grid-column: 1 / 3; 
	grid-row: 1 / 2; 
}
```

![](https://i.imgur.com/rPKszZT.png)
```
.item:nth-child(1) { 
	/* 1번 라인에서 2칸 */ 
	grid-column: 1 / span 2; 
	/* 1번 라인에서 3칸 */ 
	grid-row: 1 / span 3; 
}
```

![](https://i.imgur.com/8u1x1Ks.png)
```
.container { 
	grid-template-columns: 50px; 
	grid-auto-columns: 1fr 2fr; 
} 
.item:nth-child(1) { grid-column: 2; } .item:nth-child(2) { grid-column: 3; } .item:nth-child(3) { grid-column: 4; } .item:nth-child(4) { grid-column: 5; } .item:nth-child(5) { grid-column: 6; } .item:nth-child(6) { grid-column: 7; } 
/* end를 생략하면 그냥 한 칸임 */
```

### grid-template-areas : 영어 별칭으로 그리드 정의
- 각 영역(Grid Area)에 이름을 붙이고, 그 이름을 이용해서 배치하는 방법
- 매우 직관적

![](https://i.imgur.com/EzcjLSy.png)
```
.container { 
	grid-template-areas: 
		"header header header" 
		" a main b " " . . . " 
		"footer footer footer"; 
}
.header { grid-area: header; } 
.sidebar-a { grid-area: a; } 
.main-content { grid-area: main; } 
.sidebar-b { grid-area: b; } 
.footer { grid-area: footer; } 
/* 이름 값에 따옴표가 없는 것에 주의 */
```

### grid-auto-flow : 자동 배치
![](https://uxkm.io/_assets/images/css/grid/uxkm_grid-auto-flow-column.svg)
![](https://i.imgur.com/5yZsTsf.png)
```
.container { 
	display: grid; 
	grid-template-columns: repeat(auto-fill, minmax(25%, auto)); 
	grid-template-rows: repeat(5, minmax(50px,auto)); 
	grid-auto-flow: dense; 
} 

item:nth-child(2) { grid-column: auto / span 3; } 
item:nth-child(5) { grid-column: auto / span 3; } 
item:nth-child(7) { grid-column: auto / span 2; }
```
* row : 기본값으로 각 행을 차례로 채우고 필요에 따라 새 행을 추가하는 자동 배치
* column : 각 열을 차례로 채우고, 필요에 따라서 새 열을 추가하는 자동 배치
* dense : 배치 중 나중에 크기가 작은 아이템이 존재하는 경우, 그리드 영역 앞부분의 남은 공간에 자동 배치
* row dense : 각 행 축을 따라 차례로 배치, 빈 영역을 매꿈
* column dense : 각 열 축을 따라 차례로 배치, 빈 영역을 매꿈

### align-items : 세로방향 정렬,  justify-items : 가로 방향 정렬
![](https://i.imgur.com/nfooz9H.png)
```
.container { 
	align-items: stretch; 
	/* align-items: start; */ 
	/* align-items: center; */ 
	/* align-items: end; */ 
}
.container { 
	justify-items: stretch; 
	/* justify-items: start; */ 
	/* justify-items: center; */ 
	/* justify-items: end; */ 
}
```

### place-items : align-items와 justfy-items를 같이 쓸 수 있는 단축속성
```
.container { place-items: "align-items값" "justify-items값"; }
```

### align-content : 아이템 그룹 세로 정렬
![](https://i.imgur.com/f42WRtp.png)
```
.container { 
	align-content: stretch; 
	/* align-content: start; */ 
	/* align-content: center; */ 
	/* align-content: end; */ 
	/* align-content: space-between; */ 
	/* align-content: space-around; */ 
	/* align-content: space-evenly; */ 
}
.container { 
	justify-content: stretch; 
	/* justify-content: start; */ 
	/* justify-content: center; */ 
	/* justify-content: end; */ 
	/* justify-content: space-between; */ 
	/* justify-content: space-around; */ 
	/* justify-content: space-evenly; */ 
}
```
### place-content : align-content와 justify-content를 함께 쓸 수 있는 속성
```
.container { place-content: "align-content값" "justify-content값"; }
```

### align-self : 개별 아이템 세로 정렬, justify-self : 개별 아이템 가로 정렬
- 해당 아이템을 세로(column축) 방향으로 정렬
```
.item { 
	align-self: stretch; 
	/* align-self: start; */ 
	/* align-self: center; */ 
	/* align-self: end; */ 
}
```
### place-self : align-self와 justify-self를 동시에 쓸 수 있는 속성
```
.item { place-self: "align-self값" "justify-self값"; }
```

### Order : 배치 순서
![](https://i.imgur.com/7xdOABE.png)
```
.item:nth-child(1) { order: 3; } /* A */ 
.item:nth-child(2) { order: 1; } /* B */ 
.item:nth-child(3) { order: 2; } /* C */
```

###  z-index : z축 정렬
![](https://i.imgur.com/zGv0E4Y.png)
```
.item:nth-child(5) { 
	z-index: 1; 
	transform: scale(2); 
} 

/* z-index를 설정 안하면 0이므로, 1만 설정해도 나머지 아이템을 보다 위로 올라온다 */
```

###  IE에서 그리드를 사용하는 속성
| 일반 | IE |
| ---------------------- | -------- |
| display: grid; | display: -ms-grid; |
| grid-template-rows | -ms-grid-rows |
| grid-template-columns | -ms-grid-columns |
| grid-row-start | -ms-grid-row |
| grid-column-start|-ms-grid-column |
| grid-row: 1 / span 2;에서 span 2 대신|-ms-grid-row-span: 2 |
| grid-column: 1 / span 2;에서 span 2 대신|-ms-grid-column-span: 2 |
| align-self|-ms-grid-row-align |
| justify-self|-ms-grid-column-align |

---
### nth-child 선택자 : 해당 요소의 자식요소중 특정 번째의 요소를 선택하는 선택자
- :first-child : 해당 요소의 자식요소 중 첫번째 요소 선택
- :last-child :해당 요소의 자식요소 중 마지막 요소 선택
- :last-child(n) :해당 요소의 자식요소 중 마지막 n개의 요소 선택
- :nth-child(n) : 해당 요소의 자식요소 중 n번째 요소 선택
- :nth-child(n + k) : 해당 요소의 자식요소 중 k번째 요소부터 모두 선택
- :nth-child(-n + k) : 해당 요소의 자식요소 중 1번째 요소부터 k번째 요소까지 모두 선택
- :nth-child(n + k):nth-child(-n + l) : 해당 요소의 자식요소 중 k번째 요소부터 l번째 요소까지 모두 선택
- :nth-child(odd) : 해당 요소의 자식요소 중 n번째 요소 선택
- :nth-child(even) : 해당 요소의 자식요소 중 n번째 요소 선택
- :nth-child(kn+l) : 해당 요소의 자식요소 중 l번째 요소부터 k번째 요소마다 선택
```css
/* 첫번째 요소 선택 */
.section01 li:first-child{background:skyblue;}

/* 마지막 요소 선택 */
.section02 li:last-child{background:skyblue;}

/* 6번째 요소 선택 */
.section03 li:nth-child(6){background:skyblue;}

/* 홀수 선택 */
.section04 li:nth-child(odd){background:skyblue;}

/* 짝수 선택 */
.section05 li:nth-child(even){background:skyblue;}

/* 세번째 요소마다 선택 */
.section06 li:nth-child(3n){background:skyblue;}

/* 두번째 요소부터 세번째 요소마다 선택 */
.section07 li:nth-child(3n+2){background:skyblue;}

/* 6번부터 모든 요소 선택 */
.section08 li:nth-child(n+6){background:skyblue;}

/* 1번부터 3번까지 요소 선택 */
.section09 li:nth-child(-n+3){background:skyblue;}

/* 3번부터 6번까지 요소 선택  */
.section10 li:nth-child(n+3):nth-child(-n+6){background:skyblue;}

/* 끝에서 3번째 요소 선택 */
.section11 li:nth-last-child(3){background:skyblue;}

/* 끝에서 3번째 요소까지 선택 */
.section12 li:nth-last-child(-n+3){background:skyblue;}

/* 끝에서 3번째 요소부터 세번째 요소마다 선택 */
.section13 li:nth-last-child(3n+3){background:skyblue;}

/* 끝에서 3번째 요소부터 첫번째 요소까지 선택 */
.section14 li:nth-last-child(n+3){background:skyblue;}

/* 그룹 내 형제요소가 5개 이상일 때 전체 선택 */
.section15 li:nth-last-child(n+5),
.section15 li:nth-last-child(n+5) ~ li{background:skyblue;}

/* 그룹 내 형제요소가 3개 이하일 때 전체 선택 */
.section16 li:nth-last-child(-n+3):first-child,
.section16 li:nth-last-child(-n+3):first-child ~ li{background:skyblue;}

/* 3번째 요소만 제외하고 전체 선택 */
.section17 li:not(:nth-child(3)) {background:skyblue;}
```

### nth-of-type 선택자 : 해당 요소의 자식 요소중 특정 요소의 특정번째 요소를 선택하는 선택자
- <특정요소명> :nth-of-type 선택자
```css
/* group 내 첫번째 div 요소 선택 */
.section01 .group div:first-of-type{background:skyblue;}

/* group 내 마지막 div 요소 선택 */
.section02 .group div:last-of-type{background:skyblue;}

/* 두번째 span 요소 선택 */
.section03 .group span:nth-of-type(2){background:skyblue;}

/* 첫번째 p 요소 부터 두번째 p요소마다 선택 */
.section04 .group p:nth-of-type(2n+1){background:skyblue;}

/* 세번째 p 요소부터 전체선택 + 첫번째 p 요소부터 6개 선택의 교집합 */
.section05 .group p:nth-of-type(n+3):nth-of-type(-n+6){background:skyblue;}
```

### UTF-8  : 상단 head 태그 안에 메타태그로 추가
- html : `<meta charset="utf-8">`
- xhtml : `<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />`

## ==반응형 이해하기==
### WHY?
- 온라인 검색의 60 % 이상이 모바일 기기에서 발생
- 모든 종류의 기기에 맞는 화면을 제공하기 위해 반응형은 필수가 되어가고 있음

# 오늘의 멘토링 🥸
- Q1 : `[YANA]` spring에서 모든 request에 특정 정적 리소스를 담아서 보내줄 수 있는 방법이 있을까요?  
	Spring backend, React frontend 프로젝트에서 프론트와 백엔드 어플리게이션을 서버에서 각각 구동시키는것이 아닌, react 앱을 빌드 한 뒤 spring 어플리케이션의 정적 리소스에 담아서 보내고자 합니다. 기존에 node 프로젝트애서 동일한 방법(프론트 앱 빌드 후 백엔드 서버의 resource로 전달)을 사용했던 경우에는 특정 정적 리소스를 모든 requerst에 담아서 보내도록 설정을 할 수 있어서 관련 설정을 해주었는데, spring에서도 모든 request에 특정 리소스를 담아서 보내줄 수 있는 방법이 있을까요?
	위와 같은 방법으로 스프링 어플리케이션을 구동해보니, react앱이 빌드된 파일이 index.html이라 루트경로에 대해서는 resource폴더의 static폴더 안의 index.html를 인식하기 때문에 뷰파일이 있다고 판단해 화면을 띄워주고, GUI를 통한 화면전환은 이루어지고있는데, 다른 url을 통해 보내는 요청에 대해서는 no static resources 응답을 보내고 있습니다. 관련해서 testController를 생성해 특정 경로에 대해 index.html파일을 view로 전달하도록 설정해보니, 해당 요청에 대해서는 no resources가 아닌 view를 정상적으로 응답하고있는걸 확인했습니다. 따라서 리액트 라우팅으로 이루어진 경로들에 대해서는 index.html파일을 함께 전달해야 할 것 같아 질문드립니다.
	- A 1: servlet단에서 해당 요청에 대한 차단이 일어나고있을것이다. 따라서 servlet에서 특정 경로 이하에 대한 요청은 모두 열어주는식으로 해서 해결이 가능할 것 같긴 한데, 해당 방법은 요청을 무한으로 보낼 수 있기 때문에 보안적으로나 성능적으로 위험한 방법이다. 따라서 정적 메서드가 아닌 각각의 어플리케이션을 구동하는것을 추천한다.
	- Q1-1 : 배포에 사용할 클라우드 서버의 스케일이 제한된 상황이라,  프론트와 백엔드 어플리게이션을 서버에서 각각 구동시키는것이 아닌, react 앱을 빌드 한 뒤 spring 어플리케이션의 정적 리소스에 담아서 보내고자했습니다.
	- A 1-1 : 그렇다면 이해가 간다. 하지만 그런 경우는 흔한 경우가 아니다. 보통 운영서버의 스케일을 작게 설정하지는 않는다.
	- Q1-2 : 클라이언트 측에서 요청을 해온 건이라, 우선 시도중이었습니다. 해당 방법 관련해서 Dispatcher의 Handler Mapping단계에서 해당 요청을 처리해줄 컨트롤러가 없어 차단이 일어난다는점은 이해했습니다.
	  혹시 Custom Filter를 사용해서 특정 요청들에 대해서는 response에 index.html을 view파일로 함께 전달하라고 지정하는 방식은 가능하지 않을까 하는 생각이 드는데, 멘토님께서는 어떻게 생각하시나요?
	- A1-2 : 해당 방법으로 구현한다고 하면 아까 말했던 보안이나 성능이슈는 잡을 수 있을 것 같다. 해당 방법은 front-end 코드와 backend 코드 사이에 결합도를 높인다는 점은 유의하고 있으면 좋을 것 같다. 관련해서 mvc패턴을 가능한 줄이고자 하는 이유에 대해서도 함께 생각해보면 좋겠다.
- Q2 : `[YANA]` 이전 질문과 비슷하게, 제 개인 포트폴리오를 위핸 aws 인스턴스에서도 스케일 관련 이슈가 있어 질문드립니다.. 현재 aws 프리티어 ec2서버인 t2.micro에 docker-compose를 이용해 spring application 3개와 nginx를 띄워 리버스 프록싱을 적용함으로써 운영중입니다.
   어플리케이션을 띄울때에는 조금 느리다는 부분 말고는 정상적으로 구동이 되는데, 이틀간격으로 어플리케이션이 다운되는 현상을 마주했습니다. 
   해당 부분 관련해서 파악을 해보니, 스프링 부트 어플리케이션에서 특정 주기마다 메모리 사용량이 증가함을 확인했는데,docker-compose로 한날 한시에 모든 어플리케이션이 run되었기에 메모리 사용량도 동시에 증가하였고.. 관련해서 모든 어플리케이션이 가용 가능한 ram을 A라고 인식했지만, 사실은 A가 아닌 A를 4개의 docker-contailer에서 돌아가는 서비스들이 나눠서 사용해야 하는 부분이기에 applicaion이 종료되는것 같습니다. 관련해서 RDS측도 확인해보니 ec2서버의 어플리케이션들이 비정상 종료되기 직전 connection 이 급격하게 증가하는 현상을 확인했습니다.
   물론, 스케일이 매우 작은 서버에 무리한 설정을 해두었다는 점은 알고있으며 스케일 업이 필요하다는 점은 분명히 인지하고 있지만, 메모리와 connectionr관련 궁금증이 들어 관련해서 혹시 spring 어플리케이션의 가용 메모리에 제한을 걸어주거나, connection 생성에 제한을 두는 등의 방법으로 혹시 해당 이슈를 잡을수도 있을까요?
	- A : 물론 JVM의 메모리 사용 설정이나 hikariCP의 connection 에 대한 제한을 둘 수는 있다. 
	  해당 상황은 알다시피 스케일업이 필수인 것이, spring 어플리케이션과 nginx 그리고 RDS connection관련 이슈 뿐 아니라, 쿠버네티스가 아닌 docker를 활용하는 점에서도 발생할수밖에 없는 유실등이 있다. 
	  따라서 클라우드 환경이 아니라, 값싼 linux 컴퓨터를 중고로 구매해서 가정에서 직접 하드웨어로 서버를 운영해보는 경험을 해보는것을 추천한다. 나 또한 해당 방법으로 개인 서버를 운영했었다. 좋은 경험이 될 것이라고 본다.
	  Q2-1 : 관련해서 이전에 집에서 사용하지 않는 notebook을 이용해 포트를 열어 서버를 운영하다가, 보안이슈와 인터넷 비용이 기하급수적으로 많이 나올수 있다는 이야기를 들어 다시 모든 포트를 닫았던 상황입니다. 조금 우려가 되는데 괜찮을까요?
	- 8080, 80, 22, 443처럼 각 서비스 주력포트를 사용하지 않는다면 개인 서버에 대해서 모든 포트를 찔러보는 노력은 하지 않을것이라고 본다. 만약 당한다고 하더라도... 좋은 경험이 될것으로 본다.
	   관련해서 추천도서로  [네트워크를 훔쳐라]([https://www.yes24.com/Product/Goods/407021](https://www.yes24.com/Product/Goods/407021))를 추천한다.
- Q3 : 주니어 개발자를 위한 개발 도서 추천
	- A : 
		1. 🌟 [실용주의 프로그래머](https://product.kyobobook.co.kr/detail/S000001033128)
		2. [개발자가 반드시 알아야 할 자바 성능 튜닝 이야기](https://product.kyobobook.co.kr/detail/S000001032977)
		3. [가상 면접 사례로 배우는 대규모 시스템 설계 기초](https://product.kyobobook.co.kr/detail/S000001033116)
		4. [Node Js 교과서](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=306783871)
		5. [NestJS로 배우는 백엔드 프로그래밍]([https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=306191959](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=306191959))
		6. [마이크로 서비스 아키텍처 구축]([https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=317987700](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=317987700))
		7. [Real MySQL 8.0 1권]([https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=278488709](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=278488709))
		8. [Node.js 하이퍼포먼스]([https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=98320450](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=98320450))
		9. [혼자 공부하는 컴퓨터구조 + 운영체제]([https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=299014282](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=299014282))

## 오늘 멘토링과 관련해서 생각/공부해봐야 할 주제 🤔
1. 왜 mvc 패턴은 지양되어가는 중일까?
	- [[작고 귀여운 나의 운영서버를 위한 Spring + react 프로젝트 정적 리소스 배포기(feat.. spring servlet custom filter + 왜 mvc 패턴은 지양되고 있는가.)]]
2. filter를 통해 정적 리소스를 보내준다면, 어느 필터 다음에 위치시키는 것이 가장 적절한가 고민해봐야겠다.

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 