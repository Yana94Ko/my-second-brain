---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 4일차 (Git,& Github 활용 버전관리, HTML CSS 레이아웃과 포지셔닝)"
tistoryTags: 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistoryPostId: "217"
tistoryPostUrl: https://yanacoding.tistory.com/217
tistorySkipModal: true
---
`
오늘 수강한 강의 : [ 【한글자막】 100일 코딩 챌린지 - Web Development 부트캠프](https://www.udemy.com/course/100-2022-web-development/?utm_source=adwords&utm_medium=udemyads&utm_campaign=WebDevelopment_Search_la.KR_cc.KR&utm_term=_._ag_153638105748_._ad_644611295653_._kw__._de_c_._dm__._pl__._ti_dsa-1939216851836_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA-P-rBhBEEiwAQEXhH8I5AFNq9-SbeYPmP5uwMpj7SzsS-tWDZ-KBEI9inPiFi4XJTAO19hoCjtEQAvD_BwE)

---
# 오늘의 강의 정리 📗

---

오늘 VOD 강의(13-16일차) 진도에서는 깃과 깃허브를 통한 버전관리와, HTML CSS의 레이아웃 및 포지셔닝에 대해서 배웠다. Git, Github의 경우엔 계속해서 써왔고, 앞으로도 계속 사용할 버전관리 시스템이기 때문에 다시 한 번 복습한다는 관점에서 수강을 완료했다. HTML CSS에서도 grid와 flex처럼 요소를 배치하는 부분에서 최근 프로젝트에서 고생을 했던 부분이었기에 관심있게 수강 할 수 있었다.

## ===git, github를 통한 버전관리===
### 브랜치
- 가지 또는 분기점. 
- 보통 git을 통한 협업 혹은 개발을 할때에 주 축이 되는 브랜치의 **현재 상태를 복사**하여 ** 생성한 새로운 Branch에서 작업**을 한 후, 분기해온 브랜치의 기능이 완전하다고 판단되면 Merge를 통해 주 축이 되는 브랜치에 해당 기능을 반영한다.

### 커밋
- 현재까지 변경(추가/수정)되어 git add를 통해 Staging Area에 올라간 변경사항들을 SnapShot 하는 작업.
- '-m' 플래그를 통해 어떠한 변경인지 명시한다.

### Github
-  깃(Git)을 사용하는 프로젝트를 지원하는 웹 호스팅 서비스.
	- cf1) 깃 : 휴대폰 속 애니팡(오프라인에서도 플레이가 가능) 
	          깃허브 : 애니팡 서버(온라인 서버를 통해 유저간 하트 주고받기, 기록경쟁 외 상호작용 가능)
	- cf2) 깃(Git)사용 시 서버를 자체적으로 구축하는것도 가능하지만, Github 서버를 이용하는편이 편하다.
- 오픈소스의 경우 무료로 서버 제공 => 오픈소스의 성지
- 2019년부터 Private 소스들도 무료 업로드 가능
### github -Fork
- 오픈소스프로젝트의 저장소(repository) 를 내 Github 저장소로 복제해 오는 것을 말함.
- 오픈소스 저장소를 upstream 으로 부르고 내 Github 저장소를 origin으로 부름.
- 저장소(repository)의 브랜치 쓰기 권한이 없는 사람이 프로젝트에 대한 변경을 제안하거나 다른 사람의 프로젝트를 기반으로 자신의 아이디어를 발전시키는 것으로 사용하기 위해서 fork를 사용.

### github - PR(Pull Request)
- Fork해온 upstream 저장소 혹은 ,같은 repo 내의 타 브랜치로 merge를 하기 위해 작성하는 요청.
- 보통 로컬 저장소에서 변경사항을 push할 수 없도록 제한을 걸어놓은 브랜치로 작업내용을 병합 할 때 사용한다.
- 현재 가장 많이 사용중인 협업 방식으로는 각각 기능별 branch를 생성한뒤 작업한 내용을 dev 브랜치에 병합하며, 본인의 작업내용을 병합하기 위해서는 정해진 양식에 맞는 PR을 작성하고 협업자들에게 코드리뷰를 받은 뒤, 특정 인원수 이상이 해당 기능에 문제가 없다고 판단하고 approve하면 dev브랜치로 merge할 수 있게 설정해서 사용하고있다.

## ===HTML CSS 레이아웃과 포지셔닝===

### Flex
- Flexible Box, Flexbox라고도 부름

## Flex Container(플렉스 컨테이너)
- 부모 요소
- Flex의 영향을 받는 전체 공간
## Flex Item(플렉스 아이템)
- 자식 요소
- 설정된 속성에 따라, 컨테이너 안에 플렉스 아이템들이 특정 형태로 배치됨

##  Flex 컨테이너에 적용하는 속성
### display : flex - 요소들이 가로 방향으로 배치됨
- width : 자신이 가진 내용물의 width 만큼만 차지.
- height : 컨테이너의 높이만큼 늘어남.
### display : inline-flex : 컨테이너가 주변 요소들과 어떻게 어우러질지 결정(like inline-block)

![](https://i.imgur.com/V3BNag6.png)
### 메인축(Main Axis) : 아이템들이 배치된 방향의 축

### **수직축 또는 교차축**(Cross Axis) : 메인축과 수직이 되는 축

### flex-direction : 배치 방향 설정
```
.container { 
	flex-direction: row; 
	/* flex-direction: column; */ 
	/* flex-direction: row-reverse; */ 
	/* flex-direction: column-reverse; */ 
}
```
![](https://i.imgur.com/2Qg6oxB.png)
### flex-wrap : 줄넘김 처리 설정
```
.container { 
	flex-wrap: nowrap; 
	/* flex-wrap: wrap; */ 
	/* flex-wrap: wrap-reverse; */ 
}
```
![](https://i.imgur.com/Cnt1IBe.png)

### flex-wrap : flex-direction과 flex-wrap을 한꺼번에 지정할 수 있는 단축 속성
```
.container { 
	flex-flow: row wrap; 
	/* 아래의 두 줄을 줄여 쓴 것 */ 
	/* flex-direction: row; */ 
	/* flex-wrap: wrap; */ }
```

### justify-content : 메인축 방향 정렬
![](https://i.imgur.com/gYPToia.png)
```
.container { 
	justify-content: flex-start; 
	/* justify-content: flex-end; */ 
	/* justify-content: center; */ 
	/* justify-content: space-between; */ 
	/* justify-content: space-around; */ 
	/* justify-content: space-evenly; */ /*IE와 엣지(Edge)에서는 지원되지 않음*/ 
}
```
- flex-start : 아이템들을 시작점으로 정렬
	- flex-direction이 row(가로 배치)일 때는 왼쪽, column(세로 배치)일 때는 위
- flex-end : 아이템들을 끝점으로 정렬
	- flex-direction이 row(가로 배치)일 때는 오른쪽, column(세로 배치)일 때는 아래
- center : 아이템들을 가운데로 정렬

![](https://i.imgur.com/kvvLU3A.png)

### align-items : 수직축 방향 정렬
![](https://i.imgur.com/V0vblc8.png)
```
.container { 
	align-items: stretch; 
	/* align-items: flex-start; */ 
	/* align-items: flex-end; */ 
	/* align-items: center; */ 
	/* align-items: baseline; */ 
}
```
- stretch : 아이템들이 수직축 방향으로 끝까지 쭈욱 늘어남
- flex-start : 아이템들을 시작점으로 정렬
	- flex-direction이 row(가로 배치)일 때는 위, column(세로 배치)일 때는 왼쪽
* flex-end : 아이템들을 끝으로 정렬
	* flex-direction이 row(가로 배치)일 때는 아래, column(세로 배치)일 때는 오른쪽
- center : 아이템들을 가운데로 정렬
- baseline : 아이템들을 텍스트 베이스라인 기준으로 정렬

![](https://i.imgur.com/6cXT6Mf.png)
### align-content : 여러 행 정렬
```
.container { 
	flex-wrap: wrap; 
	align-content: stretch; 
	/* align-content: flex-start; */ 
	/* align-content: flex-end; */ 
	/* align-content: center; */ 
	/* align-content: space-between; */ 
	/* align-content: space-around; */ 
	/* align-content: space-evenly; */ 
}
```
![](https://i.imgur.com/3Nz3RFp.png)


## Flex 아이템에 적용하는 속성
### flex-basis : Flex 아이템의 기본 크기를 설정
- flex-direction이 row일 때는 너비, column일 때는 높이
```
.item { 
flex-basis: auto; /* 기본값 */ 
	/* flex-basis: 0; */ 
	/* flex-basis: 50%; */ 
	/* flex-basis: 300px; */ 
	/* flex-basis: 10rem; */ 
	/* flex-basis: content; */ 
}
```
- 관련해서 영역 width제한이 넘어갔을 시 개행하도록 하려면 **word-wrap: break-word;** 설정
### flex-grow : 아이템이 flex-basis의 값보다 커질 수 있는지를 결정
- "유연하게 늘리기"
- 숫자값이 들어가는데, 몇이든 일단 0보다 큰 값이 세팅이 되면 해당 아이템이 유연한(Flexible) 박스로 변하고 원래의 크기보다 커지며 빈 공간을 메우게 됨.
- 숫자의 의미 : 아이템들의 flex-basis를 제외한 **여백** 부분을 **flex-grow에 지정된 숫자의 비율**로 나누어 가진다고 생각하면 됨.
```
/* 1:2:1의 비율로 세팅할 경우 */ 
.item:nth-child(1) { flex-grow: 1; } 
.item:nth-child(2) { flex-grow: 2; } 
.item:nth-child(3) { flex-grow: 1; }
```
![](https://i.imgur.com/4QUJYFe.png)

### flex-shrink : 아이템이 flex-basis의 값보다 작아질 수 있는지를 결정
- "유연하게 줄이기"
- 숫자값이 들어가는데, 몇이든 일단 0보다 큰 값이 세팅이 되면 해당 아이템이 유연한(Flexible) 박스로 변하고 flex-basis보다 작아짐.
- 기본값이 1이기 때문에 따로 세팅하지 않았어도 아이템이 flex-basis보다 작아질 수 있음.
- 0으로 세팅하면 아이템의 크기가 flex-basis보다 작아지지 않기 때문에 고정폭의 컬럼을 쉽게 만들 수 있음.
```
.item { flex-basis: 150px; flex-shrink: 1; /* 기본값 */ }
```
### flex : flex-grow, flex-shrink, flex-basis를 한 번에 쓸 수 있는 축약형 속성
```
.item { 
	flex: 1; /* flex-grow: 1; flex-shrink: 1; flex-basis: 0%; */ 
	flex: 1 1 auto; /* flex-grow: 1; flex-shrink: 1; flex-basis: auto; */ 
	flex: 1 500px; /* flex-grow: 1; flex-shrink: 1; flex-basis: 500px; */ 
}
```

```
.container { 
	display: flex; 
	flex-wrap: wrap; 
} 
.item { 
	flex: 1 1 40%; 
}
```

![](https://i.imgur.com/3270rME.png)

### align-self : 해당 아이템의 수직축 방향 정렬
- 수직으로 아이템 정렬
```
.item { 
	align-self: auto; 
	/* align-self: stretch; */ 
	/* align-self: flex-start; */ 
	/* align-self: flex-end; */ 
	/* align-self: center; */ 
	/* align-self: baseline; */ 
}
```
![](https://i.imgur.com/g1KGwX4.png)
### order : 각 아이템들의 시각적 나열 순서를 결정하는 속성
- “시각적” 순서일 뿐, HTML 자체의 구조를 바꾸는 것은 아니므로 접근성 측면에서 사용에 주의해야 함.
```
.item:nth-child(1) { order: 3; } /* A */ 
.item:nth-child(2) { order: 1; } /* B */ 
.item:nth-child(3) { order: 2; } /* C */
```

### z-index : Z축 정렬
- 숫자가 클 수록 위

---
# 오늘의 멘토링 🥸

- Q1 : git 브랜치 관리 전략 관련 질문 드립니다 :)브랜치 관리 전략의 일종으로 git flow와 github flow가 존재하고, 웹 애플리케이션 개발에는 github flow가 유리하다는 글을 읽게 되었습니다. 제게는 아직 두 개념 모두 생소하지만, 멘토님께서는 웹 앱 개발에 github flow가 더 유리하다고 생각하시는지요? 만약 그렇게 생각하신다면 이유도 궁금합니다!
	- A : 요약 - 속해있는 조직의 크기에 따라서 유리한 전략이 다를 것 같다. github-flow의 경우엔 구성원이 많지 않은 경우에 유리할 것 같고, 조직의 규모가 커지게 된다면 git-flow가 유리 할 수 있을 것 같다.
	- 물론 두 flow가 정답이고 해당 flow만을 따라야한다는건 아니다. 
- Q2 : TDD에 대한 글을 읽었는데, 효과적으로 실무에 적용하기 위해 고민하는 기업이 있는 반면 실제로 적용하기에는 시간이나 여러가지 요인으로 제약이 있다는 의견도 있었습니다. TDD에 대한 멘토님의 생각이 궁금하고, 혼자 사이드프로젝트로 경험을 하는 것이 도움이 될지 여쭤보고 싶습니다. (프론트, 백 양쪽 관점 모두에서 설명해주시면 감사하겠습니다!)
	- 추천글 : [# TDD is dead. Long live testing.](https://dhh.dk/2014/tdd-is-dead-long-live-testing.html)
- Q3 : TDD 관련 내용이 나와서, DDD에 대해서 질문드리고자 합니다! 말로는 익히 들었는데 정확한 개념은 알지 못해서, DDD(Domain의 D)란 무엇인지! 에 대해서 질문드립니다ㅎㅎ
	- 추천도서 : [객체지향의 사실과 오해](https://product.kyobobook.co.kr/detail/S000001628109)
	- 추천도서 : [오브젝트](https://product.kyobobook.co.kr/detail/S000001766367)

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 