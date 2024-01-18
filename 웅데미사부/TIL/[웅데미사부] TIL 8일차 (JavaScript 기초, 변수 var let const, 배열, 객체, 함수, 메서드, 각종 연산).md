---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 8일차 (JavaScript 기초, 변수 var let const, 배열, 객체, 함수, 메서드, 각종 연산)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "225"
tistoryPostUrl: https://yanacoding.tistory.com/225
---
오늘 수강한 강의 : [ 【한글자막】 100일 코딩 챌린지 - Web Development 부트캠프](https://www.udemy.com/course/100-2022-web-development/?utm_source=adwords&utm_medium=udemyads&utm_campaign=WebDevelopment_Search_la.KR_cc.KR&utm_term=_._ag_153638105748_._ad_644611295653_._kw__._de_c_._dm__._pl__._ti_dsa-1939216851836_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA-P-rBhBEEiwAQEXhH8I5AFNq9-SbeYPmP5uwMpj7SzsS-tWDZ-KBEI9inPiFi4XJTAO19hoCjtEQAvD_BwE)

---
# 오늘의 강의 정리 📗

# ==자바스크립트 기초 이해하기==

## 자바스크립트란?
- 웹 페이지에서 복잡한 기능을 구현 할 수 있는 스크립팅 또는 프로그래밍 언어.
- 보통 스크립트 언어 혹은 인터프리터 언어로 분류됨.
- JavaScript 코드는 JavaScript엔진에 의해 해석(기본 기계어로 직접 변환)됨.
	- JavaScript 엔진 : JavaScript 코드를 실행하는 컴퓨터 프로그램.
		- (최초 JS엔진) 단순한 인터프리터 -> JIT(Just-In-Time)또는 런타임 컴파일을 통해 성능 향상
	- 클라이언트 측 JS : JS 가 브라우저에서 작동하는 방식을 나타냄.
		- 이 경우 JS 엔진은 브라우저 코드 내부에 위치.
			- 모든 주요 브라우저에는 JS 엔진이 내장되어 있음.
	- 서버 측 JS : 백엔드 서버 로직에서 코딩언어로 JS를 사용함.
		- 이 경우 JS 엔진은 서버에 직접 위치.
		- 서버측 JS함수는 데이터 베이스에 엑세스 하고, 논리작업을 수행하는 등의 작업 수행
			- 장점 : 요구 사항, 액세스 권한 및 웹 사이트의 정보 요청에 따라 웹 사이트 응답을 쉽게 사용자 지정할 수 있음.
- 웹 브라우저에서 JS 가 동작하는 방식
	1. 웹 페이지 방문 시 브라우저가 웹 페이지 로드
	2. 로드하는 동안 브라우저는 버튼, 레이블, 드롭다운 박스와 같은 페이지 및 모든 요소를 문서 객체 모델(DOM)이라는 데이터 구조로 변환함.
	3. 브라우저의 JS 엔진은 JS 코드를 바이트 코드로 변환시킴.
	4. 버튼에 대한 마우스 클릭과 같은 다양한 이벤트는 연결된 JS 코드 블록의 실행을 트리거함.
		- 이후 JS 엔진은 바이트 코드를 해석해서 DOM을 변경함.
	5. 브라우저에 새 DOM이 표시됨.
- 서버에서의 JS (Node.js)
	- 브라우저 외부에서 JavaScript 코드를 실행하는 서버 측 오픈 소스 JavaScript 프레임워크
	- 확장 가능하고 빠르며 안정적인 네트워크 기반의 서버 측 애플리케이션을 구축
	- HTTP 요청 및 데이터 스트림을 처리하고, 파일 시스템을 지원하며, 여러 백엔드 프로세스를 동시에 관리
### HTML : (마크업 언어)문단, 제목, 데이터 표를 정의하거나 페이지에 이미지와 동영상을 삽입하는 등 웹 콘텐츠를 구성하고 의미를 부여
### CSS : (스타일 규칙 언어)배경색과 글꼴을 설정하고 콘텐츠를 여러 열에 배치하는 등 HTML 콘텐츠에 스타일을 적용하는 데 사용
### Javascript : (스크립팅 언어)동적으로 변경되는 콘텐츠를 만들고, 멀티미디어를 제어하고, 이미지에 애니메이션을 적용하는 등 거의 모든 작업을 수행


## HTML 요소 - script
1. Script 태그 내 인라인 스크립트 작성
```
<head>
	<script>
		//수행할 작업
	</srcipt>
</head>
```
2. 외부에서 정의한 JS 적용
```
<head>
	<script scr="파일경로+파일명.js">//절대 아무 내용도 넣지 마시오</srcipt>
</head>
```
### CF) 빠른 렌더링과 UX(User Experience)를 위한 JS, CSS 호출 위치
### 1) 브라우저 렌더링 과정
![](https://i.imgur.com/5Mth4Rx.png)
- 브라우저는 HTML, CSS, JS, 이미지, 폰트 파일 등 렌더링에 필요한 리소스를 요청하고 서버로부터 응답을 받음
- 브라우저의 렌더링 엔진은 서버로부터 응단된 HTML, CSS를 파싱하여 DOM과 CSSOM을 생성하고 이들을 결합해 렌더 트리 생성
- 브라우저의 자바스크립트 엔진은 서버로부터 응답된 자바스크립트를 파싱하여 AST를 생성하고 바이트코드로  변환해 실행. 자바스크립트는 DOM API를 통해 DOM이나 CSSOM을 변경할 수 있음. 변경된 DOM과 CSSOM은 다시 렌더 트리로 결합
- 렌터 트리를 기반으로 HTML 요소의 레이아웃(위치와 크기)을 계산하고 브라우저 화면에 HTML 요소를 페인팅
- `*` 이 때 HTML 문서 파싱 중 CSS 요소 혹은 Script요소가 있다면 브라우저 엔진은 HTML 파싱을 멈추고 해당 요소를 먼저 읽게 됨.
### 2) 적절한 stylesheet, script 위치
- CSS : 늦게 호출 될 경우 사용자는 스타일이 적용되지 않은 화면을 볼 수 있음.
	- 따라서, stylesheet의 호출은 head요소에 있는것이 좋은
- JS : Script 파일이 head 요소이고 용량이 크다면 body 요소의 실행이 늦어지게 됨.
	- 따라서, 사용자가 빈 화면만 보면서 대기하는 불상사를 막기 위해 body 태그의 최하단에 두는 편.

## 변수(variable) : 하나의 값을 저장하기 위해 확보한 메모리 공간 자체 또는 그 메모리 공간을 식별하기 위해 붙인 이름
- 자바스크립트는 매니지드 언어(managed language)
	- 개발자가 직접 메모리를 제어하지 못함.
	- 개발자가 직접 메모리 주소를 통해 값을 저장하고 참조할 필요가 없음.
	- 변수를 통해 안전하게 값에 접근이 가능.

- 변수에 값을 저장하는 것을 **할당**(assignment, 대입, 저장)이라 하며 변수에 저장된 값을 읽어 들이는 것을 **참조**(reference)라고 함.

- **변수의 선언** :  `var`, `const`, `let` 키워드로 할 수 있으며, ES6에서 const와 let이 추가됨.
	- 자바스크립트에서 변수 선언은 `선언 → 초기화` 단계를 거쳐 수행
		- **선언 단계**: 변수명을 등록하여 자바스크립트 엔진에 변수의 존재를 알림.
		- **초기화 단계**: 값을 저장하기 위한 메모리 공간을 확보하고 암묵적으로 undefined를 할당해 초기화

- 변수의 할당 : 할당 연산자(=)를 사용

## var, let, const
### var의 문제점 
- 변수 중복 선언 가능하여, 예기치 못한 값을 반환할 수 있음
- 함수 레벨 스코프로 인해 함수 외부에서 선언한 변수는 모두 전역 변수로 됨
- 변수 선언문 이전에 변수를 참조하면 언제나 undefined를 반환
### let : 변수 중복 선언 불가
- 변수 중복 선언이 불가하지만, 재할당은 가능
```
let name = 'kmj'
console.log(name) // output: kmj

let name = 'howdy' // output: Uncaught SyntaxError: Identifier 'name' has already been declared

name = 'howdy'
console.log(name) // output: howdy

```
### const(상수) : 반드시 선언과 초기화를 동시에 진행
- 재선언 불가하며,  재할당도 불가
	- 재할당의 경우, 원시 값은 불가능하지만, 객체는 가능
	- 재할당을 금지할 뿐, '불변'을 의미하지 않음
```
const name; // output: Uncaught SyntaxError: Missing initializer in const declaration
const name = 'kmj'
// 원시값의 재할당
const name = 'kmj'
name = 'howdy' // output: Uncaught TypeError: Assignment to constant variable.

// 객체의 재할당
const name = {
  eng: 'kmj',
}
name.eng = 'howdy'

console.log(name) // output: { eng: "howdy" }
```

## 호이스팅
- 인터프리터가 코드를 실행하기 전에 함수, 변수, 클래스 또는 임포트(import)의 선언문을 해당 범위의 맨 위로 이동시키는 과정
	- var 변수는 호이스팅 지원(파일 어디에서 선언을 하고 할당을 하건 상관없이 사용 가능)
	- let 변수는 호이스팅 미지원(상단에서 선언 및 할당이 완료되어야 아래에서 사용 가능)

## 자료형
### 원시 자료형 : 한번에 하나의 값만 가질 수 있는 자료형
- 하나의 고정된 저장 공간을 이용합니다.
- 종류 : 
	- null
	- undefined
	- boolean
	- string
	- number
	- bigint
	- symbol
### 참조 자료형 : 한번에 여러 개의 값을 가질 수 있는 자료형
- 여러 개의 고정되지 않은 동적 공간을 사용합니다.
- 종류 : 
	- Object
	- Array
	- Function

## 객체 : 모든 값이 속성으로 저장되는 관련 값의 그룹
### 객체의 선언
- 여러개의 관계된 변수를 선언 할 때 아래와 같이 작성 가능
```
let jobtTitle = 'Developer'; 
let jobPlace = 'New York'; 
let jobSalary = 50000;
```
- 아래와 같이 객체로 선언 가능
```
let job = { 
	title: 'Developer', 
	place: 'New York', 
	salary: 50000 
};
```
### 객체의 사용
- 그룹명.요소명 형태로 사용
```
let job = { 
	title: 'Developer', 
	place: 'New York', 
	salary: 50000
}; 
alert(job.title);
```
### 전역 객체
- 브라우저 환경 : window
- Node.js : global
## 배열
### 배열의 선언
```
let hobbies = ["coding", "karaoke", "reading", 1, 2]; 
```
### 배열의 사용(인덱싱)
```
hobbies[0];
```

## 함수(function)
### 함수의 선언과 사용
- 선언 : function 함수명 ( 매개변수 ) { 수행할 작업 }
- 사용 : 함수명(매개변수
- return을 활용해 활용성을 높일 수 있음
```
let age = 26; 
let adultYears; 

function calcualteAdultYears(){ 
	adultYears = age - 18; 
} 

calcualteAdultYears(); 
alert(adultYears); 

age = 45; 
calcualteAdultYears(); 
alert(adultYears);
```
### 콜백함수
```
const checkMood = (mood, goodCallback, badCallback)  
{  
    if (mood === "good") goodCallback();  
    else badCallback();  
}  
  
const cry = () => console.log("ACTION :: CRY");  
const sing = () => console.log("ACTION :: SING");  
const dance = () => console.log("ACTION :: DANCE");  
  
checkMood("sad", sing, cry);
```

## 메서드(method) : 객체의 원소로 들어간 함수를 메서드라 지칭
- cf) 메서드가 아닌 원소들 :  property
```
// 객체 및 메서드 선언부 
let person = { 
	name: "Justin", 
	// 메서드 정의시 function 키워드를 붙이지 않음
	greet() { 
		alert("Hello!"); 
	} 
} 
// 호출부 
person.greet();
```

### console.log
- 정보 출력을 위해 사용
- 브라우저의 개발자 모드 콘솔 창을 통해 확인 가능
### 수학 연산 & 다양한 종류의 값 작업
```
//수학 연산
console.log(10+4); 
console.log(10-4); 
console.log(10*4); 
console.log(10/4); 
console.log(10%4);

// 증감연산
let result = 10; 
result++; 
console.log(result); 
result--; 
console.log(result); 
result+=5; 
console.log(result);

//문자열 연산
console.log('java'+'script'); 
console.log('javascript'-'java');
let userName = 'Max'; 
console.log(userName.length); 
console.log(userName.toUpperCase());

//배열 작업
let hobbies =['Sports', 'Cooking']; 
console.log(hobbies.length);
```


---
# 오늘의 멘토링 🥸
- Q1 : `[YANA]` 멘토님 spring에서 사용해보지 못했던 기능들을 마음껏 사용해보려고 개인 spring playground 프로젝트를 만들어서 멀티모듈을 시도해본다던가, spring security를 적용해본다던가 하는 식으로 사용중인데, 이런 부분도 어떻게 보면 포트폴리오로써 사용 할 수도 있는걸까요?
	- A : 면접자 대부분은 개발덕후. 기술을 단순히 써보기만 한 것으로는 약하다. 궁금한 기능을 직접 프로젝트에서 써먹보는 같은 수준의 기술덕후를 원한다.
- Q2 :  `[YANA]` Spring boot application에서 파일과 여러 정보가 담긴 json 데이터를 하나의 api로 전달받아서 파일의 S3업로드 후 업도르 파일의 url을 여타 정보들과 함께 담아 하나의 entity에 저장하려했습니다. frontend에서 content-type을 multipart/formdata로 명시하고 파일을 담아서 보내줬으며, spring boot application에서는 @RequestPart 어노테이션을 활용해 file과 json데이터를 Request 객체에 담으려 시도했습니다. 하지만 spring boot 에서 application/octet-stream type 컨텐츠를 처리 할 수 없다는 응답을 계속해서 보내왔고, 관련해서 확인해보니 controller조차 타지 않는 상황이라 AbstractJackson2HttpMessageConverter를 extend 받아 해당 타입 다룰 수 있는 converter를 생성해주니 동작하는 상황입니다. 관련해서 컨버터 제거하고 HttpServletRequest로 받은뒤 file과 json을 각각 꺼내보니 정상 동작하는 상황인데, 컨버터를 사용하는 방법도 그리고 request로 받는 방법도 온전히 납득이 가지 않아 걱정이 됩니다. 보통 현업에서는 관련 상황을 어떻게 처리하시나요?
	- A : 각각 다른 타입의 데이터를 보내주는것이기 때문에 api를 분리하는 것이 맞다고 봄.
		더불어서 파일 업로드의 경우에는 비동기로 처리 할 수 있도록 한 뒤, 해당 업로드에 대한 키를 다른 api 호출시 사용해서 연계를 지어준다던가 하는 방식으로 구현을 하는게 맞다고 판단됨. 관련해서 임시저장소는 필수로 사용하게 될 것. api를 분리한다는 관점으로 다시 생각해보길.
## 오늘 멘토링과 관련해서 생각/공부해봐야 할 주제 🤔
1. 각각 다른 타입의 데이터를 보내주는 때에는 하나의 요청에 두가지 이상의 데이터 형식을 담는 것은(param 제외) "HTTP 표준에 어긋나기 때문"에 api를 분리하는것이 좋다고 하셨는데..
	1) "HTTP 표준에 어긋난다"는건 뭘까?
	2) 두가지 타입의 데이터를 하나의 요청에 보내는건 정말 HTTP 표준에 어긋날까?
2. 파일 업로드의 경우 비동기로 하는게 좋겠다고 하셨는데, 이유가 뭘까?
	- 실패시 재시도하는 로직을 짜기 위해서일까?
3. JSON과 file이라는 두가지 타입 데이터를 하나의 요청에서 전달한 경우, 프론트에서 보낸 요청의 contentType가 아닌 다른 contentType으로 servlet단에 들어오게 되는것 같은데, 어떤 과정이 있었길래 바뀐걸까? 
	- cf) [[front에서는 multipart formdata로 보내준 request가 spring에서는 application octet-stream이 되어 돌아오는 마법]]

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 