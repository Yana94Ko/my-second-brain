---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 10일차 (제어구조, 패키지작업)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "236"
tistoryPostUrl: https://yanacoding.tistory.com/236
---
오늘 수강한 강의 : [ 【한글자막】 100일 코딩 챌린지 - Web Development 부트캠프](https://www.udemy.com/course/100-2022-web-development/?utm_source=adwords&utm_medium=udemyads&utm_campaign=WebDevelopment_Search_la.KR_cc.KR&utm_term=_._ag_153638105748_._ad_644611295653_._kw__._de_c_._dm__._pl__._ti_dsa-1939216851836_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA-P-rBhBEEiwAQEXhH8I5AFNq9-SbeYPmP5uwMpj7SzsS-tWDZ-KBEI9inPiFi4XJTAO19hoCjtEQAvD_BwE)

---
# 오늘의 강의 정리 📗

# 제어구조, 제어구문
- 프로그램의 논리 구조를 표현할 수 있는 **조건문과 반복문**, 그리고 그 밖에 프로그램의 논리 구조에 영향을 미치는 구문

![](https://i.imgur.com/9oZXdSi.png)

# Boolean 연산자
- 값 : true , false (진리값)
```js
1 < 2; // true
1 > 2; // false
3 === 3; // true
3 !== 3; // false
Number.isFinite(Infinity); // false
Number.isNaN(NaN); // true
'hello'.includes('ll'); // true
```
# 비교 연산자
# 논리 연산자
- js는 진리값에 대한 여러 연산을 지원
## 논리 연산
```js
// 논리 부정 (logical NOT)
!true; // false
!false; // true

// 논리합 (logical OR)
true || true; // true
true || false; // true
false || true; // true
false || false; // false

// 논리곱 (logical AND)
true && true; // true
true && false; // false
false && true; // false
false && false; // false

// 할당 연산 (assignment operators), ES2021
// ||= 는 변수의 값이 true이면 아무 변화가 일어나지 않고 false이면 우항의 값이 변수에 할당됩니다.
let x = false;
x ||= true; // true

// &&= 는 변수의 값이 false이면 아무 변화가 일어나지 않고 true이면 우항의 값이 변수에 할당됩니다.
let y = true;
y &&= false; // false

// ||=와 &&=는 각각 아래 연산과 같은 동작을 합니다.
x = x || true
y = y && false

// 삼항 연산자 (ternary operator)
true ? 1 : 2; // 1
false ? 1 : 2; // 2
```
## 논리 연산의 여러가지 법칙
- cf) [연산자 우선순위](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Operator_precedence)
```js
// a, b, c가 **모두 boolean 타입**이라고 할 때, 다음 식의 결과값은 a, b, c의 값과 관계 없이 모두 true 입니다.

// 이중 부정
!!a === a;

// 교환 법칙
a || b === b || a;
a && b === b && a;

// 결합 법칙
(a || b) || c === a || (b || c);
(a && b) && c === a && (b && c);

// 분배 법칙
a || (b && c) === (a || b) && (a || c);
a && (b || c) === (a && b) || (a && c);

// 흡수 법칙
a && (a || b) === a;
a || (a && b) === a;

// 드 모르간의 법칙
!(a || b) === !a && !b;
!(a && b) === !a || !b;

// 그 밖에...
a || true === true;
a || false === a;
a && true === a;
a && false === false;

a || !a === true;
a && !a === false;

a || a === a;
a && a === a;
```

# 동등 연산자(`==`)
- 두 개의 피연산자가 동일한지 확인하며, 불리언 결과를 반환
- 다른 타입의 피연산자들끼리의 비교를 시도(값만 같으면 true)
```js
let a = 10;

let b = '10';

console.log(a == b);    // true

console.log('' == '0');    // false
console.log('' == 0);    // true
console.log('0' == 0);    // true
console.log('false' == false);    // false
console.log('0' == false);    // true
console.log(0 == false);    // true
console.log(null == undefined);    // true
console.log(null == false);    // false
console.log(undefined == false);    // false

let val1 = null;
let val2 = undefined;

if (val1 == null && val1 == undefined) {
    console.log('val1 is null and undefined');
}
if (val2 == null && val2 == undefined) {
    console.log('val2 is null and undefined');
}

console.log(null == undefined);   // true
console.log(null == false); // false
console.log(null == 0); // false
console.log(null == '');  // false
console.log(undefined == false);  // false
console.log(undefined == 0);  // false
console.log(undefined == '');  // false
```
# 일치 연산자(`===`)
- 두 개의 피연산자가 동일한지 확인하며, 불리언 결과를 반환
- 값과 타입이 모두 같은 경우에만 true
	- 서로 다른 유형의 피연산자는 다른 것으로 간주.
```js
let a = 10;
let b = '10';
let c = 10;

console.log(a == b);  // true
console.log(a === b); // false
console.log(a === c); // true

//NaN은 서로 다른 값으로 판단하기 때문에, isNaN 이용해야 함
console.log(NaN === NaN);  // false
console.log(isNaN(NaN)); // true

//0과 -0은 같은 값으로 취급
console.log(0 === -0);  // true
```
# Truthy / Falsy
- JavaScript에서는 boolean 타입이 와야 하는 자리에 다른 타입의 값이 와도 에러가 나지 않고 실행됨
- Falsy : false, null, undefined, 0, NaN, ''.
- Truthy : Falsy 값을 제외한 모든 값들은 Truthy로 취급됨.

# 반복문
## for문
- 어떤 특정한 조건이 거짓으로 판별될 때까지 반복
- begin : 반복문에 진입할 때 단 한 번 실행됩니다.
- condition : 반복마다 해당 조건이 확인됩니다. false이면 반복문을 멈춥니다.
- body : condition이 truthy일 동안 계속해서 실행됩니다.
- step : 각 반복의 body가 실행된 이후에 실행됩니다.
```js
for (begin; condition; step) {
  // ... 반복문 본문 ...
}
```
### 인라인 변수 선언
```js
for (let i = 0; i < 3; i++) { // 0, 1, 2가 출력됩니다.
  alert(i);
}
```
### 정의되어있는 변수를 사용
```js
let i = 0;

for (i = 0; i < 3; i++) { // 기존에 정의된 변수 사용
  alert(i); // 0, 1, 2
}

alert(i); // 3, 반복문 밖에서 선언한 변수이므로 사용할 수 있음
```
### 구성 요소 생략
```js
// begin 생략
let i = 0; // i를 선언하고 값도 할당하였습니다.

for (; i < 3; i++) { // 'begin'이 필요하지 않기 때문에 생략하였습니다.
  alert( i ); // 0, 1, 2
}

// step까지 생략
let i = 0;

for (; i < 3;) {
  alert( i++ );
}

//3) 모든 구성요소 생략
for (;;) {
  // 끊임 없이 본문이 실행됩니다.
}
```
## for in 문 : object, 배열
- 배열에는 사용을 추천하지 않음
```javascript
const obj = {
  name : '이름',
  age : '나이'
}

for(const key in obj){
  console.log(key); // key값 출력
  console.log(obj.name, obj.age); // value 값 출력

  console.log(`key 값 : ${key}`); // 1. key값 : 이름 // 2. key값 :age
  console.log(`value 값 : ${obj[key]}`); // 1. value 값 : 이름 // 2. value값 : 나이
}
```

## for of 문 : 반복 가능한 객체
- 반복 가능한 객체(Array, Map, Set, String, TypedArray, arguments 객체 등 포함)에 대해 사용
```js
const array = ['1번', '2번', '3번'];

for(const element of array) {
  console.log(element); // 배열[0] ~ 끝까지 순차적 출력
  console.log(array); // 배열 전체 출력
}
```

## forEach() : 배열
- 인자에 콜백함수를 넣어 사용
```js
onst array = ['1번', '2번', '3번'];

array.forEach((element)=>{
  console.log(element);
})
```
## while 문
- 조건이 참이면 실행되는 반복문
```js
while(condition) {
  // condition이 참이면 실행
}
```
## do while문
- `do{}`에 작성된 코드는 최소 1번 실행
```js
do {
	// 거짓이더라도
  //do에 작성된 코드는 무조건 1회는 실행
}while(condition)
```
## break(반복문 빠져 나가기)
- 반복문의 경우, 대개는 반복문의 조건이 falsy가 되면 반복문이 종료
- break를 사용하면 언제든 반복문을 빠져나올 수 있음
```js
let sum = 0;

while (true) {

  let value = +prompt("숫자를 입력하세요.", '');

  if (!value) break; // (*)

  sum += value;

}
alert( '합계: ' + sum );
```

## continue(다음 반복문으로 넘어가기)
- 현재 실행 중인 이터레이션을 멈추고 반복문이 다음 이터레이션을 강제로 실행시킴
- `continue`는 현재 반복을 종료시키고 다음 반복으로 넘어가고 싶을 때 사용
```js
for (let i = 0; i < 10; i++) {

  // 조건이 참이라면 남아있는 본문은 실행되지 않습니다.
  if (i % 2 == 0) continue;

  alert(i); // 1, 3, 5, 7, 9가 차례대로 출력됨
}
```
## label : 중첩 반복문에서 원하는 반복문을 빠져나오는 방법
```js
labelName: for (...) {
  ...
}

outer: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    let input = prompt(`(${i},${j})의 값`, '');
    // 사용자가 아무것도 입력하지 않거나 Cancel 버튼을 누르면 두 반복문 모두를 빠져나옵니다.
    if (!input) break outer; // (*)
    // 입력받은 값을 가지고 무언가를 함
  }
}
alert('완료!');
```

# Third-Party Packages
![](https://i.imgur.com/ji1fFZk.png)
![](https://i.imgur.com/nT9UrVS.png)

# 반복문
# CSS 패키지
![](https://i.imgur.com/WSW7NeJ.png)

# JS 패키지
![](https://i.imgur.com/DDyq601.png)

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 