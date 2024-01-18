---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 6일차 (반응형 웹 디자인 이해하기, 멋있는 웹사이트 만들기)"
tistoryTags: 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistoryPostId: "219"
tistoryPostUrl: https://yanacoding.tistory.com/219
---

오늘 수강한 강의 : [ 【한글자막】 100일 코딩 챌린지 - Web Development 부트캠프](https://www.udemy.com/course/100-2022-web-development/?utm_source=adwords&utm_medium=udemyads&utm_campaign=WebDevelopment_Search_la.KR_cc.KR&utm_term=_._ag_153638105748_._ad_644611295653_._kw__._de_c_._dm__._pl__._ti_dsa-1939216851836_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA-P-rBhBEEiwAQEXhH8I5AFNq9-SbeYPmP5uwMpj7SzsS-tWDZ-KBEI9inPiFi4XJTAO19hoCjtEQAvD_BwE)

---
# 오늘의 강의 정리 📗

## em : 해당 단위가 사용되고 있는 요소의 `font-size` 속성값에 비례해서 결정되는 상대 단위
- `font-size` : `20p`
	- `0.5em = 20 px x 0.5 = 10px`
	- `1em = 20 px x 1 = 20px`
	- `2em = 20 px x 2 = 40px`
	- `3em = 20 px x 3 = 60px`
- `font-size` : `10px`
	-  `0.5em = 10 px x 0.5 = 5px`
	- `1em = 10 px x 1 = 10px`
	- `2em = 10 px x 2 = 20px`
	- `3em = 10 px x 3 = 30px`

## rem : `html` 요소의 `font-size` 속성값이 기준
- `rem`에서 `r`은 `root`
- HTML에서 최상위 요소는 `<html>`이기 때문에 rem의 기준은 html
- `rem` 단위를 사용하면 해당 요소의 `font-size` 속성값은 전혀 중요하지않게 됨

## [CSS 값과 단위](https://developer.mozilla.org/ko/docs/Learn/CSS/Building_blocks/Values_and_units)

## 모바일 퍼스트 디자인
- 모바일 사용자 경험을 최우선으로 고려하여 웹사이트 또는 앱을 디자인하는 접근 방식
- 간결하고 단순한 레이아웃
- 모바일 친화적 네비게이션
- 반응형 이미지
- 터치 피드백
- 속도 최적화 외
- 장점 :  SEO 향상, 사용자 경험 개선, 사용자 참여 증가 외
- 단점 : 데스크톱 사용자 경험이 안좋아 질 수 있음, 콘텐츠의 제약 등등

## 미디어 쿼리
- 화면 해상도, 기기 방향 등의 조건으로 HTML에 적용하는 스타일을 전환할 수 있는 CSS3의 속성 중 하나
### 기본 문법
```
@media [only 또는 not] [미디어 유형] [and 또는 ,] (조건문) {실행문}
```
### `[`only 또는 not 또는 and`]
- and : 미디어 쿼리 조건 추가
- only : 미디어 쿼리가 호환되는 브라우저에서만 인식 가능하도록 설정
- not : not 뒤에 지정하는 미디어 유형은 제외함
### 미디어 유형
- all : 모든 미디어 유형
- screan : 컴퓨터 스크린
- tv : 텔레비전
- handheld : 패드 장치
- braille : 점자 표시 장치

## HTML 프레그먼트
- 같은 페이지(html)파일에서 특정 섹션으로 이동할 때 사용.
- 이동해 가기를 원하는 요소의 id 를 href의 경로에 넣어주면, 클릭시 해당 요소의 위치로 스크롤이 이동함.

## [target](https://developer.mozilla.org/en-US/docs/Web/CSS/:target) 선택자 : 가상 선택자의 한 종류
- HTML 프레그먼트를 통해 해당 요소로 이동함으로써 URL에 해당 아이디가 추가상태일 때 적용할 CSS를 설정 할 수 있다.
```
p:target {
  display : none;
}
```

---
# 오늘의 멘토링 🥸
- Q1 : `[Y군]`코딩테스트 결과로,**채점 상 높은 점수** (즉, 높은 정확성과 효율성) vs (가독성 및 재사용성 측면에서**) 높은 코드 퀄리티.** (단, 비교적 낮은 점수)두명의 지원자의 코딩테스트 결과가 위와 같이 나왔고, 다른 모든 조건이 동일하다는 가정하에 한명만을 합격시켜야 한다면 누굴 뽑으실지 궁금합니다ㅎㅎ실제로 코딩 테스트에 응시하게 되면 시간적인 압박을 받을 때가 많은데요, 당연히 위 두가지를 모두 갖추면 좋겠지만 우선적인 초점을 어디에 두고 준비하는 것이 좋을지 알고싶어서 질문을 드립니다.
	- A : 요구사항을 해내는 사람이 일머리가 있다는 판단이 든다. 후자의 경우엔 코드의 퀄리티에 만족하지 못하면 일정 내에 요구사항을 해내지 못할수도 있을것 같다는 느낌이 들기도 한다.
	  코딩테스트 관점에서 만약 알고리즘과 코드에 대한 이해를 강조하고싶다면, 주석을 통해 시간복잡도 등을 설명함으로써 해당 문제의 의도를 파악하고있다는 것을 어필하는 방법도 있다.
- Q2 : 신입 개발자와 경력 개발자를 뽑을 때의 주요 평가항목이 다를 것 같습니다. 멘토님의 경험에서 신입 개발자를 뽑을 때 중점적으로 보았던 항목, 경력 개발자를 뽑을 때 중점적으로 보았던 항목에 대해서 궁금합니다.그리고 면접관의 입장을 많이 경험해보셨을 것 같은데, 가장 인상깊었던 지원자나 뽑고 싶지 않았던 지원자에 대한 멘토님의 생각과 그 이유에 대해서 알고 싶습니다.
	- A : 신입에 대한 요구사항이 올라가기는 했지만, 잘하는 신입보다는 앞으로 많이 성장 할 것 같은 개발자를 채용하는 편이다. 그 뿐만 아니라 기존 구성원과의 캐미나 업무의 맥락을 잘 이해 할 것 같으면서, 기존 구성원의 피드백을 잘 수용하고 해당 피드백의 포인트를 이해하는지 여부를 판단한다. 이 사람을 설득하기 힘들겠다는 판단이 든다면 채용에서 후순위가 될 수 있다. 태도나 이해력 논리력, 근거 기본의 사고를 지닌 신입을 뽑으려 하는 편이다.

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 