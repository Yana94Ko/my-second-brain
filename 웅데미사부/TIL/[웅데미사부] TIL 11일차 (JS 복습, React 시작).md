---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 11일차 (JS 복습, React 시작)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "237"
tistoryPostUrl: https://yanacoding.tistory.com/237
---
오늘 수강한 강의 : [# 【한글자막】 React 완벽 가이드 with Redux, Next.js, TypeScript](https://www.udemy.com/course/best-react/?utm_source=adwords&utm_medium=udemyads&utm_campaign=Webindex_Catchall_la.KR_cc.KR&utm_term=_._ag_154831691911_._ad_667917181863_._kw__._de_c_._dm__._pl__._ti_dsa-1456167871416_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=Cj0KCQiAv8SsBhC7ARIsALIkVT0YQL1Z1xCLn5v8iq06aTV-vGZOOgmozcCu1fIQne3Vm82noB_KqDQaAp61EALw_wcB)

---
# 오늘의 강의 정리 📗

# [React](https://react.dev/)란?
- User Interface를 만들기 위한 JS 라이브러리(Facebook_현재Meta에서 만들었다.)
1. 웹 개발이 복잡해짐에 따라 html, css, js만으로는 한계가 생겼으며, 초기에는 Web 개발을 위한 프론트엔드 라이브러리로 DOM조작을 쉽게해주는 jQuery 라이브러리가 주로 사용되었음
2. DOM을 직접 조작하는 방식에 한계를 느껴 대규모 프로젝트에 효율적으로 코드를 관리하고, 컴포넌트 기반 UI 개발을 지원하는 프론트엔드 프레임워크(라이브러리)가 등장
   - Angular, React, Vue를 프론트엔드 개발을 대표하는 도구 3가지라 부름
	   - Angular, Vue : 개발에 필요한 전체적인 구조와 규칙을 제공(프레임워크)
	   - React : 용자 인터페이스의 개발을 돕는 도구와 기능을 제공(라이브러리)

# Vanila JS 가 아닌 React를 사용하는 이유
- UI를 자동으로 업데이트해주기 때문에 UI를 빠르게 업데이트할 수 있음
- 가상 돔(Virtual Dom)을 통해 재사용이 필요한 기능을 언제든지 필요한 곳에서 호출
- 반복적인 코드 작성 없이 사용할 수 있도록 해줌
- JS 기반의 문법을 사용하기 때문에 JS에 익숙하다면 보다 쉽게 사용
- 가볍고 유연한 라이브러리로, 필요한 부분에만 적용할 수 있음
- 활발하고 다양한 커뮤니티와 생태계를 가지고 있음
- 리액트의 UI를 만드는 기능을 확장하여 웹이 아닌 플랫폼에서 활용할 수 있도록 기술을 확장
	- React Native는 안드로이드(Android)와 아이폰(iOS)의 모바일 앱을 만드는 대표적인 기술
![(출처: 유데미 React 완벽 가이드 with Redux, Next.js, TypeScript )](https://i.imgur.com/hqslkm9.png)
![(출처: 유데미 React 완벽 가이드 with Redux, Next.js, TypeScript )](https://i.imgur.com/IZqeX95.png)
![(출처: 유데미 React 완벽 가이드 with Redux, Next.js, TypeScript )](https://i.imgur.com/mi6QtEB.png)

# JS 복습
## 모듈 - import & export
### 모듈
- 개발하는 app이 커지면 어느 순산 파일을 여러개로 분리해야하는 순간이 옴
- js 에서 분리된 파일 각각을 모듈(module)라고 부름
- 보통 클래스 하나나 혹은 특정한 목적을 가진 복수의 함수로 구성된 라이브러리 하나로 구성
### export
- 파일이나 모듈 안의 함수나 객체를 export 할 때 사용
- Named exports와 Default exports 두가지 방법이 있음
- 부모 모듈이 자식 모듈을 가져와서 다시 내보낼 수도 있음
	- 즉, 여러개의 모듈을 모아놓을 하나의 모듈을 만들 수 있음.
		- 각각의 reducer 을 만든 다음 하나의 super reducer를 만든것을 생각하면 될듯
```js
// 변수, 함수 선언식을 하나씩 export
export let name1, name2, …, nameN; // var, const도 동일
export let name1 = …, name2 = …, …, nameN; // var, const도 동일
export function functionName(){...}
export class ClassName {...}


// 변수명, 함수명을 모아 멤버 목록으로 export
export { name1, name2, ..., nameN };
export { variable1 as name1, variable2 as name2, ..., nameN }; // 별칭으로 export


// 비구조화로 내보내기
export const { name1, name2: bar } = o;


// default export
export default expression;
export default function (…) { … } // also class, function*
export default function name1(…) { … } // also class, function*
export { name1 as default, … };
```
#### Named export :  여러값을 export 하는데 유용
```js
export const arrs = [10, 20, 30, 40]; // 개별로 선언해서 export

export { arrs2, getName }; // 묶어서 export

const arrs2 = [100, 200, 300, 400];
function getName() {
    return "aaaaaaaaa";
}
```
#### Default export : 모듈당 딱 1개의 default export만 있어야 함
- 딱 한개만 default export를 할 수 있기 때문에, "메인" 이라고 할 수 있는 것을 default export 하는 것이 좋음
```js
let cube = function cube(x) {
    return x * x * x;
}
export default cube;
```

### import
- 외부 스크립트 또는 외부 모듈의 export된 함수, 객체를 가져오는데 사용
```js
// named
import * as name from "module-name";
import name from "module-name";
import { member } from "module-name";
import { member as alias } from "module-name"; // member이름이 길 경우 as 별명 가능
import { member1, member2 } from "module-name";
import { member1, member2 as alias2, [...] } from "module-name";


// default
import defaultMember, { member [, [...]] } from "module-name";
import defaultMember, * as alias from "module-name";
import defaultMember from "module-name";
import "module-name";
/*
   name : 가져온 값을 받을 객체 이름.
   member, memberN : export 된 모듈에서 멤버의 이름
   defaultMember : export 된 모듈의 default 이름
   alias, aliasN : export된 멤버의 이름을 지정한 이름
   module-name : 가져올 모듈 이름 (파일명)
*/
```
#### 모듈 전체 가져오기
```js
import * as myModule from "my-module.js";
// myModule.sayHello()
```
#### 한개의 멤버 가져오기
```js
import {myMember} from "my-module.js";
```
#### 여러개의 멤버 가져오기
```js
import {myMember} from "my-module.js";
```
#### 다른 이름으로 멤버 가져오기
```js
import {reallyReallyLongModuleMemberName as shortName} from "my-module.js";
import {reallyReallyLongModuleMemberName as shortName, anotherLongModuleName as short} from "my-module.js";
```
#### 바인딩 없이 모듈 실행만 하기
```js
import "my-module.js";
```
#### default export 값 가져오기
```js
import myModule from "my-module.js";
```
#### 브라우저(HTML)에서 모듈 사용하기
- 모듈 스크립트는 항상 지연 실행
	- 다운로드할 때 브라우저의 HTML 처리가 멈추지 않음
- 모듈 비동기 처리
	- async 속성이 붙은 스크립트 태그 로딩이 끝나면 다른 스크립트나 HTML 문서가 처리되길 기다리지 않고 바로 실행
```js
<!DOCTYPE html>

<script type="module">
    import {sayHi} from './say.js';

    document.body.innerHTML = sayHi('John');
</script>
```
## null과 undefined
### undefined : 변수를 선언하고 값을 할당하지 않은 상태
- 원시값(Primitive Type)
- typeof : undefined(자료형이 없음)
- 예시
	- 값을 할당하지 않은 변수
	- 메서드와 선언에서 변수가 할당받지 않은 경우
	- 함수가 값을 return 하지 않았을 때
### null : 변수를 선언하고 빈 값을 할당한 상태(빈 객체)
- 원시값(Primitive Type) 중 하나
- 어떤 값이 의도적으로 비어있음을 표현
- typeof : object
- null은 undefined처럼 전역 객체의 속성 중 하나가 아니라 리터럴 값
- undefined == null : true

## 변수 명명 규칙과 컨벤션
![(출처: 유데미 React 완벽 가이드 with Redux, Next.js, TypeScript )](https://i.imgur.com/QLNsbxz.png)

## 함수, 그리고 파라미터 디폴트 값
```js
// 파라미터에 디폴트 값을 부여할 수 있다
function createGreeting(userName, message = "Hello!") {
  //   console.log(userName);
  //   console.log(message);
  return userName + ", " + message;
}

console.log(createGreeting("Yana"));
console.log(createGreeting("Yana", "how's it going?"));
```

## 화살표 함수(Arrow Function)
- 함수 표현식보다 단순하고 간결한 문법으로 함수를 만드는 방법
- 화살표 함수의 선언
	- 인자 arg1..argN를 받는 함수 func
	- 화살표(=>) 우측의 표현식(expression)을 평가하고, 평가 결과를 반환
```js
//기존 함수
let func = function(arg1, arg2, ...argN) {
  return expression;
};
//화살표 함수
let func = (arg1, arg2, ...argN) => expression
```
### 인수가 1개인 화살표 함수
- 괄호 생략
```js
let double = n => n * 2;
// let double = function(n) { return n * 2 }과 거의 동일합니다.

alert( double(3) ); // 6
```
### 인수가 없는 화살표 함수
- 인수가 하나도 없을 땐 괄호를 비움
```js
let sayHi = () => alert("안녕하세요!");

sayHi();
```
### 본문이 여러줄인 화살표 함수
```js
let sum = (a, b) => {  // 중괄호는 본문 여러 줄로 구성되어 있음을 알려줍니다.
  let result = a + b;
  return result; // 중괄호를 사용했다면, return 지시자로 결괏값을 반환해주어야 합니다.
};

alert( sum(1, 2) ); // 3
```

## 클래스(Class)
-  동일한 종류의 객체를 여러 개 생성해야 하는 경우에 사용
### 클래스의 생성
```js
class MyClass {
  // 여러 메서드를 정의할 수 있음
  constructor() { ... }
  method1() { ... }
  method2() { ... }
  method3() { ... }
  ...
}
```
### 클래스의 사용
- 자바스크립트에서 클래스는 함수의 한 종류
```js
class User {

  constructor(name) {
    this.name = name;
  }

  sayHi() {
    alert(this.name);
  }

}

// 사용법:
let user = new User("John");
user.sayHi();
// User가 함수라는 증거
alert(typeof User); // function
```
- new User("John")를 호출하면...
	1. 새로운 객체가 생성됩니다.
	2. 넘겨받은 인수와 함께 constructor가 자동으로 실행됨
		- 이때 인수 "John"이 this.name에 할당됨
	3. 이런 과정을 거친 후에 user.sayHi() 같은 객체 메서드를 호출할 수 있음
### [클래스 심화 참조](https://ko.javascript.info/class)
## 배열과 내장 함수
### 배열 선언
```js
// 선언
let arr = new Array();
let arr = [];

// 초기 요소와 함께 선언
let fruits = ["사과", "오렌지", "자두"];
```
### 배열 내 특정 요소를 얻는 법
```js
let fruits = ["사과", "오렌지", "자두"];

alert( fruits[0] ); // 사과
alert( fruits[1] ); // 오렌지
alert( fruits[2] ); // 자두
```
### JS 에서 배열에는 요소의 자료형 제약이 없음
```js
// 요소에 여러 가지 자료형이 섞여 있습니다.
let arr = [ '사과', { name: '이보라' }, true, function() { alert('안녕하세요.'); } ];

// 인덱스가 1인 요소(객체)의 name 프로퍼티를 출력합니다.
alert( arr[1].name ); // 이보라

// 인덱스가 3인 요소(함수)를 실행합니다.
arr[3](); // 안녕하세요.
```
### 배열 수정
```js
fruits[2] = '배'; // 배열이 ["사과", "오렌지", "배"]로 바뀜
```
### 배열 새로운 요소 추가
```js
fruits[3] = '레몬'; // 배열이 ["사과", "오렌지", "배", "레몬"]으로 바뀜
```
### 배열 길이
```js
let fruits = ["사과", "오렌지", "자두"];

alert( fruits.length ); // 3
```
### 배열 전체 요소 출력
```js
let fruits = ["사과", "오렌지", "자두"];

alert( fruits ); // 사과,오렌지,자두
```
### [배열 기본 함수](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

#### pop
- 배열 뒷부분 값 삭제
#### push
- 배열 뒷부분에 값 삽입
#### shift
- 배열 앞부분 값 삭제
#### unshift
- 배열 앞부분에 값 삽입
#### map
- 배열의 각 원소별로 지정된 함수를 실행한 결과로 구성된 새로운 배열을 반환한다.
#### filter
- 지정된 함수의 결과 값을 true로 만드는 원소들로만 구성된 별도의 배열을 반환한다.
#### find
#### findIndex
#### reduce
- 누산기(accumulator) 및 배열의 각 값(좌에서 우로)에 대해 (누산된) 한 값으로 줄도록 함수를 적용
#### concat
- 다수의 배열을 합치고 병합된 배열의 사본을 반환
#### splice( index, 제거할 요소 개수, 배열에 추가될 요소 )
- 배열의 특정 위치에 요소를 추가하거나 삭제
#### slice ( startIndex, endIndex)
- startIndex부터 endIndex까지(endIndex는 불포함)에 대한 shallow copy를 새로운 배열 객체로 반환
#### reverse
- 배열의 원소 순서를 거꾸로 바꾼다.
#### forEach
- 배열의 각 원소별로 지정된 함수를 실행한다.
#### some
- 지정된 함수의 결과가 true일 때까지 배열의 각 원소를 반복
#### every 
- 배열의 모든 요소가 제공한 함수로 구현된 테스트를 통과하는지를 테스트
#### sort
- 배열의 원소를 알파벳순으로, 또는 지정된 함수에 따른 순서로 정렬한다. 모든 원소를 문자열로 취급해 사전적으로 정렬
#### join
- 배열 원소 전부를 하나의 문자열로 합침

## [구조 분해 할당(destructuring)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식
```js
var a, b, rest;
[a, b] = [10, 20];
console.log(a); // 10
console.log(b); // 20

[a, b, ...rest] = [10, 20, 30, 40, 50];
console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40, 50]

({ a, b } = { a: 10, b: 20 });
console.log(a); // 10
console.log(b); // 20

// Stage 4(finished) proposal
({ a, b, ...rest } = { a: 10, b: 20, c: 30, d: 40 });
console.log(a); // 10
console.log(b); // 20
console.log(rest); // {c: 30, d: 40}
```
## [스프레드 연산자(전개 구문)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
- 배열이나 문자열과 같이 반복 가능한 문자를 0개 이상의 인수 (함수로 호출할 경우) 또는 요소 (배열 리터럴의 경우)로 확장하여, 0개 이상의 키-값의 쌍으로 객체로 확장시킴
### 함수 호출
```js
myFunction(...iterableObj);
```
### 배열 리터럴과 문자열
```js
[...iterableObj, "4", "five", 6];
```
### 객체 리터럴
```js
let objClone = { ...obj };
```

## 함수를 값으로 사용하기
- 함수의 파라미터로 함수(C의 함수포인터와 유사)를 전달하고 함수 구현부에서 파라미터로 받은 함수를 실행할 수 있음
```js
function outerFn(innerFn) {
  innerFn();
}

outerFn(() => console.log("calling innerFn"));
```

## 함수 내부에서 함수 정의하기
- 자바스크립트만 사용하여 개발하는 경우엔 잘 쓰이지 않는 패턴이나,
- 리액트를 활용할 때에 자주 사용
```js
function outerFn() {
  function innerFn() {
    console.log("calling innerFn");
  }
  innerFn();
}

outerFn();
```

## 참조형(reference)과 기본 값(primitive)
![](https://i.imgur.com/43zUc6x.png)

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 