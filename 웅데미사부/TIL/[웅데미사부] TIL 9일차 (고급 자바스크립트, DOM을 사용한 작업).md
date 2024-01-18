---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 9일차 (고급 자바스크립트, DOM을 사용한 작업)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "234"
tistoryPostUrl: https://yanacoding.tistory.com/234
---
오늘 수강한 강의 : [ 【한글자막】 100일 코딩 챌린지 - Web Development 부트캠프](https://www.udemy.com/course/100-2022-web-development/?utm_source=adwords&utm_medium=udemyads&utm_campaign=WebDevelopment_Search_la.KR_cc.KR&utm_term=_._ag_153638105748_._ad_644611295653_._kw__._de_c_._dm__._pl__._ti_dsa-1939216851836_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=CjwKCAiA-P-rBhBEEiwAQEXhH8I5AFNq9-SbeYPmP5uwMpj7SzsS-tWDZ-KBEI9inPiFi4XJTAO19hoCjtEQAvD_BwE)

---
# 오늘의 강의 정리 📗

# 전역변수 window
- 브라우저에 활성화된 윈도우와 관련된 많은 유틸리티 정보과, 기능이 저장되어있음.
- 브라우저의 탭을 의미하기도 함.
- 보안상의 이유로 웹사이트에서 코드를 실행할 때에는 윈도우 객체를 이용해 현재 열고있는 탭의 정보에 엑세스 해야함(다른탭 X)
- 브라우저 안의 모든 요소들이 소속된 객체로, 최상위에 있기 때문에 어디서든 접근이 가능(전역 변수임)

- var을 이용해 전역 변수를 만들면 window 객체에 key와value가 저장됨.
	- let , const 사용시 window 객체에 추가되지 않음.
```
var a = "apple"; 
console.log(window.a);      //"apple"

let b = "banana"; 
console.log(window.b);      //undefined

const c = "strawberry";
console.log(window.c);      //undefined
```

## **window객체의 대표적인 속성**
- closed 
- console
- defaultStatus
- document
- frameElement
- frames
- history
- innerWidth
- length
- localStorage
- location
- name
- navigator
- opener
- outerHeight
- outerWidth
- pageXOffset
- pageYOffset
- parent
- screen
- screenLeft
- screenTop
- screenX
- screenY
- sessionStorage
- scrollX
- scrollY
- self
- status
- top
## **window객체의 메서드**
- alert()
- atob() : base-64로 암호화된 문자열을 암호해독
- blur() : 현재 창에서 focus 제거
- btoa() : base064로 문자열을 암호화
- clearIInterval() : setInterval()로 설정된 타이머 지우기
- clearTimeout() : setTImeout()으로 설정된 타이머 지우기
- close()
- confirm()
- focus()
- getComputedStyle()
- getSelection()
- matchMedea()
- moveBy()
- moveTo()
- open()
- print()
- prompt()
- requestAnimationFrame()
- resizeBy()
- resizeTo()
- scroll()
- scrollBy()
- scrollTo()
- setInterval() :지정된 간격(밀리초)로 함수를 호출하거나 표현식을 평가
- setTimeout() : 지정된 밀리초 후에 함수를 호출하거나 표현식을 평가
- stop() : 창 로드 정지
# 전역변수 document
- 웹페이지 그 자체를 의미
- DOM트리의 최상위 객체
	- 웹페이지에 존재하는 HTML 요소에 접근하고자 할 때에는 반드시 Doocument객체로부터 시작해야 함.
## **document객체의 역할**
- property로 HTML 문서의 전반적인 특성을 나타냄
- 메소드로 DOM 객체 검색
- 메소드로 새로운 DOM객체 생성
- 메소드로 HTML문서의 전반적  제어 지원
## **document 객체의 주요 property**
- title
- body
- head
- URL
- location
- refferr
## **document객체의 주요 컬렉션**
- images
- links
- forms
## **docment객체의 주요 메서드**
- getElementyId() : 아이디 명으로 첫번째 DOM 객체 반환
- getElementyTagName() : 특정 태그명을 가진 모든 태그 컬렉션을 반환
- getElementyClassName() : 특정 클래스명을 가진 모든 클래스 컬렉션 반환
- querySelector() : 제공된 CSS 선택자(ID 선택자, 태그 유형 선택자, 클래스 선택자, 결합 선택자 등)에 의해 충족/선택된 첫번째 HTML 요소를 선택
- 객체.onclick=funtion(){실행할 코드} : 이벤트 핸들러 추가
- open() : 모든 컨텐츠를 지우고 새로운 HTML 콘텐츠를 쓸 수 있도록 엶
- write(), writeln() : document에 HTML 콘텐츠 삽입.
- close() : document객체에 있는 HTML 콘텐츠를 브라우저에 출력하고 더이상 쓰기 입력을 받지 않음.
- createElement("태그 이름") : (동적 HTML 문서 구성) HTML 태그의 DOM 객체를 생성하는 코드.
- 부모객체.appendChild(DOM객체) : 부모객체에 마지막 자식으로 삽입
- 부모객체.insertBefore(DOM객체, `[`, 기준자식`]`) : 기준자식 앞에 삽입
- 부모객체.removeChild(자식객체) : 자식객체 삭제

# [DOM](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction)(Document Object Model) 문서 객체 모델
- 문서 객체 모델(DOM, Document Object Model)은 XML이나 HTML 문서에 접근하기 위한 일종의 인터페이스
- 문서 내의 모든 요소를 정의하고, 각각의 요소에 접근하는 방법을 제공
- 즉, 자바스크립트 같은 스크립팅 언어가 쉽게 웹페이지에 접근하여 조작 할 수 있게끔 연결시켜주는 역할.

![](https://i.imgur.com/WLGNBDG.png)


- DOM의 종류
	- Core DOM : 모즌 문서 타입을 위한 DOM 모델
	- HTML DOM : HTML문서를 위한 DOM 모델
		- HTML 문서의 계층적 구조와 정보를 표현하며, 이를 제어 할 수 있는 API, 즉 프로퍼티와 메서드를 제공하는 **트리 자료구조**
	- XML DOM : XML문서를 위한 DOM 모델

# HTML 과 DOM
![](https://i.imgur.com/Iv2jQti.png)
- console.dir(document) : 자바스크립트 object를 확인 할 수 있는 방법.

# 스크립트를 올바르게 로드하기
- 이전날에 다루었던 styledComponent와 script를 올바른 때에 호출하는 방법도 JS안의 코드와 DOM요소의 로드 순서가 영향을 주지 않도록 하는 방법 중 하나지만, script태그를 head안에 위치시키면서 스크립트 실행을 페이지 로딩보다 후순위로 지정하는 방법도 있다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FQP5X6%2FbtrnDnS5vIv%2FG8okRNfciVSbojXBwD3gb1%2Fimg.png)
## script태그 - defer 속성
- 페이지가 모두 로드된 후에 해당 외부 스크립트가 실행됨
- 보통 DOM 전체가 필요한 스크립트나 실행 순서가 중요할 때(B 스크립트는 A 스크립트 이후에 실행되어야 할 때) 적용
## script태그 - async 속성
- 브라우저가 페이지를 파싱되는 동안에도 스크립트가 실행됨
- 방문자 수 카운터 혹은 광고 스크립트 등과 같이 독립적으로 작동하는 스크립트에 적용

- async 속성은 명시되어 있지 않고 defer 속성만 명시된 경우
	- 브라우저가 페이지의 파싱을 모두 끝내면 스크립트가 실행됨
- async 속성과 defer 속성이 모두 명시되어 있지 않은 경우 : 브라우저가 페이지를 파싱하기 전에 스크립트를 가져와 바로 실행

# DOM 드릴링
- DOM객체의 속성(ex.. firstElementChild)을 통해 DOM을 탐색하는 작업

# Node 탐색
## 자식 노드 탐색
### Node.prototype.hasChildNodes :
  (텍스트 노드 포함)자식 노드 존재 확인(true / false)
### 탐색할요소명.children.length :
  (텍스트 노드를 제외한) 자식 요소 노드 존재여부 확인(true/false)
### 탐색할요소명.childElementCount :
  (텍스트 노드를 제외한) 자식 요소 노드 존재여부 확인(숫자/0false)
### Node.prototype.childNodes : 
  자식 노드를 모두 탐색하여 DOM컬렉션 객체인 NodeList에 담아 반환.
  `*` NodeList에는 요소 노드 뿐 아니라 텍스트 노드도 포함되어 있을 수 있음
### Element.prototype.children :
  자식 노드 중 요소 노드만 탐색하여 DOM컬렉션 객체인 HTMLCollection에 담아 반환
  `*` HTMLCollection에는 텍스트 노드가 포함되지 않음.

## 부모 노드 탐색
### Node.prototype.parentNode 
  cf) 텍스트 노드는 부모노드일 수 없다. 텍스트 노드는 DOM트리의 리프노드(최종단 노드)이기 때문.

## 형제 노드 탐색
### Node.prototype.previousSibling
  텍스트 노드를 포함한 노드 중 자신의 이전 형제 노드를 탐색해 HTMLElement를 상속받은 객체를 반환한다.
### Node.prototype.nestSibling
  텍스트 노드를 포함한 노드 중 자신의 다음 형제 노드를 탐색해 HTMLElement를 상속받은 객체를 반환한다.
### Element.prototype.previousElementSibling
   요소 노드 중 자신의 이전 형제 노드를 탐색해HTMLElement를 상속받은 객체를  반환한다.(IE9 이상의 브라우저에서 동작)
### Element.prototype.nextElementSibling 
  요소 노드 중 자신의 다음 형제 노드를 탐색해 HTMLElement를 상속받은 객체를 반환한다.(IE9 이상의 브라우저에서 동작)

## Node 정보  취득
### Node.prototype.nodeType 
- 노드 객체의 종류 즉 노드 타입을 나타내는 상수 반환
	- Node.ELEMENT_NODE : 1
	- Node.TEXT_NODE : 3
	- Node.DOCUMENT_NODE : 9
### Node.prototype.nodeName:
- 노드의 이름을 문자열로 반환
	- 요소노드 : 대문자 문자열로 태그이름("UL", "LI",.) 반환
	- 텍스트 노드 : "`#`text" 반환
	- 문서 노드 : "`#`document" 반환

## text node 접근 / 수정
### Node.prototype.nodeValue
- 텍스트 노드가 아닌 노드를 참조하면 null을 반환
- setter, getter 모두 존재하는 접근자 프로퍼티
- 즉, nodeValue에 값을 할당하면 노드의 값 즉 텍스트를 변경 할 수 있음.

# HTML 콘텐츠 조작(Manipulation)
- HTML 콘텐츠를 조작(Manipulation)하기 위해 아래의 프로퍼티 또는 메소드를 사용할 수 있음.
-  마크업이 포함된 콘텐츠를 추가하는 행위는 [크로스 스크립팅 공격(XSS: Cross-Site Scripting Attacks)](https://namu.wiki/w/XSS)에 취약하므로 주의가 필요
## textContent(IE9 이상)
- 요소의 텍스트 콘텐츠를 취득 또는 변경(마크업은 무시됨)
- textContent를 통해 새로운 텍스트를 할당하면, 텍스트를 변경 할 수 있음.
	- 순수한 텍스트만 지정해야 함
	- 마크업을 포함시키면 문자열 그대로 출력됨
```
<!DOCTYPE html>
<html>
  <head>
    <style>
      .red  { color: #ff0000; }
      .blue { color: #0000ff; }
    </style>
  </head>
  <body>
    <div>
      <h1>Cities</h1>
      <ul>
        <li id="one" class="red">Seoul</li>
        <li id="two" class="red">London</li>
        <li id="three" class="red">Newyork</li>
        <li id="four">Tokyo</li>
      </ul>
    </div>
    <script>
    const ul = document.querySelector('ul');

    // 요소의 텍스트 취득
    console.log(ul.textContent);
    /*
            Seoul
            London
            Newyork
            Tokyo
    */

    const one = document.getElementById('one');

    // 요소의 텍스트 취득
    console.log(one.textContent); // Seoul

    // 요소의 텍스트 변경
    one.textContent += ', Korea';

    console.log(one.textContent); // Seoul, Korea

    // 요소의 마크업이 포함된 콘텐츠 변경.
    one.textContent = '<h1>Heading</h1>';

    // 마크업이 문자열로 표시된다.
    console.log(one.textContent); // <h1>Heading</h1>
    </script>
  </body>
</html>
```

## innerText
- 요소의 텍스트 콘텐츠에 접근 가능
- 사용하지 않는 것이 좋음
	- 비표준 사항이기 때문
	- CSS에 순종적(CSS에 의해 visibility:hidden으로 지정되어 있다면, 텍스트가 반환되지 않음)
	- CSS를 고려해야함으로 textContent보다 느림

## innerHTML
- 해당 요소의 모든 자식요소를 포함하는 모든 콘텐츠를 하나의 문자열로 취득 가능(문자열 포함)
- 해당 프로퍼티를 사용해 마크업이 포함된 새로운 콘텐츠를 지정하면 새로운 요소를 DOM에 추가 할 수 있음
	- 마크업이 포함된 콘텐츠를 추가하는 것은 [크로스 스크립팅 공격(XSS: Cross-Site Scripting Attacks)](https://namu.wiki/w/XSS)에 취약
```
const ul = document.querySelector('ul');

// innerHTML 프로퍼티는 모든 자식 요소를 포함하는 모든 콘텐츠를 하나의 문자열로 취득할 수 있다. 이 문자열은 마크업을 포함한다.
console.log(ul.innerHTML);
// IE를 제외한 대부분의 브라우저들은 요소 사이의 공백 또는 줄바꿈 문자를 텍스트 노드로 취급한다
/*
        <li id="one" class="red">Seoul</li>
        <li id="two" class="red">London</li>
        <li id="three" class="red">Newyork</li>
        <li id="four">Tokyo</li>
*/
```

```
const one = document.getElementById('one');

// 마크업이 포함된 콘텐츠 취득
console.log(one.innerHTML); // Seoul

// 마크업이 포함된 콘텐츠 변경
one.innerHTML += '<em class="blue">, Korea</em>';

// 마크업이 포함된 콘텐츠 취득
console.log(one.innerHTML); // Seoul <em class="blue">, Korea</em>
```

```
// 크로스 스크립팅 공격 사례

// 스크립트 태그를 추가하여 자바스크립트가 실행되도록 한다.
// HTML5에서 innerHTML로 삽입된 <script> 코드는 실행되지 않는다.
// 크롬, 파이어폭스 등의 브라우저나 최신 브라우저 환경에서는 작동하지 않을 수도 있다.
elem.innerHTML = '<script>alert("XSS!")</script>';

// 에러 이벤트를 발생시켜 스크립트가 실행되도록 한다.
// 크롬에서도 실행된다!
elem.innerHTML = '<img src="#" onerror="alert(\'XSS\')">';
```

# DOM 조작
- HTML 콘텐츠 조작의 경우 여러 제한점(리스크)가 있기 때문에 보통 화면의 동적 변화가 필요한 경우 아래처럼 DOM을 직접 조작함
	1. 요소 노드 생성 createElement() 메소드를 사용하여 새로운 요소 노드를 생성한다. createElement() 메소드의 인자로 태그 이름을 전달한다.
	2. 텍스트 노드 생성 createTextNode() 메소드를 사용하여 새로운 텍스트 노드를 생성한다. 경우에 따라 생략될 수 있지만 생략하는 경우, 콘텐츠가 비어 있는 요소가 된다.
	3. 생성된 요소를 DOM에 추가 appendChild() 메소드를 사용하여 생성된 노드를 DOM tree에 추가한다. 또는 removeChild() 메소드를 사용하여 DOM tree에서 노드를 삭제할 수도 있다.
## createElement(tagName)
- 태그 이름을 인자로 전달하여 요소를 생성
- HTMLElement를 상속받은 객체 반환
## createTextNode(text)
- 텍트스를 인자로 전달, 텍스트 노드 생성
- Text객체 반환
## appendChild(Node)
- 인자로 전달한 노드를 마지막 자식 요소로 DOM트리에 추가
- 추가한 노드 반환
## insertBefore(Node, `[`, 기준자식`]`)
- 인자로 전달한 노드를 DOM트리에서 기준자식의 앞쪽에 추가
## removeChild(Node)
- 인자로 전달한 노드를 DOM트리에서 제거
```
// 태그이름을 인자로 전달하여 요소를 생성
const newElem = document.createElement('li');
// const newElem = document.createElement('<li>test</li>');
// Uncaught DOMException: Failed to execute 'createElement' on 'Document': The tag name provided ('<li>test</li>') is not a valid name.

// 텍스트 노드를 생성
const newText = document.createTextNode('Beijing');

// 텍스트 노드를 newElem 자식으로 DOM 트리에 추가
newElem.appendChild(newText);

const container = document.querySelector('ul');

// newElem을 container의 자식으로 DOM 트리에 추가. 마지막 요소로 추가된다.
container.appendChild(newElem);

const removeElem = document.getElementById('one');

// container의 자식인 removeElem 요소를 DOM 트리에 제거한다.
container.removeChild(removeElem);
```
# insertAdjacentHTML(position, string)
- 인자로 전달한 텍스트를 HTML로 파싱하고 그 결과로 생성된 노드를 DOM트리의 지정된 위치에 삽입.
- position 종류
	- 'beforebegin'
	- 'afterbegin'
	- 'beforeend'
	- 'afterend'
```
<!-- beforebegin -->
	<p>
		<!-- afterbegin -->
			foo
		<!-- beforeend -->
	</p>
<!-- afterend -->
```
```
const one = document.getElementById('one');

// 마크업이 포함된 요소 추가
one.insertAdjacentHTML('beforeend', '<em class="blue">, Korea</em>');
```

# innerHTML vs. DOM 조작 vs. insertAdjacentHTML()
## **innerHTML**

|장점|단점|
|---|---|
|DOM 조작 방식에 비해 빠르고 간편하다.|XSS공격에 취약점이 있기 때문에 사용자로 부터 입력받은 콘텐츠(untrusted data: 댓글, 사용자 이름 등)를 추가할 때 주의하여야 한다.|
|간편하게 문자열로 정의한 여러 요소를 DOM에 추가할 수 있다.|해당 요소의 내용을 덮어 쓴다. 즉, HTML을 다시 파싱한다. 이것은 비효율적이다.|
|콘텐츠를 취득할 수 있다.||

## **DOM 조작 방식**

|장점|단점|
|---|---|
|특정 노드 한 개(노드, 텍스트, 데이터 등)를 DOM에 추가할 때 적합하다.|innerHTML보다 느리고 더 많은 코드가 필요하다.|

## **insertAdjacentHTML()**

|장점|단점|
|---|---|
|간편하게 문자열로 정의된 여러 요소를 DOM에 추가할 수 있다.|XSS공격에 취약점이 있기 때문에 사용자로 부터 입력받은 콘텐츠(untrusted data: 댓글, 사용자 이름 등)를 추가할 때 주의하여야 한다.|
|삽입되는 위치를 선정할 수 있다.||

## **결론**
>i**nnerHTML**과 insertAdjacentHTML()은 **크로스 스크립팅 공격(XSS: Cross-Site Scripting Attacks)에 취약**
>따라서 untrusted data의 경우, 주의하여야 한다. 

>***텍스트를 추가 또는 변경**시에는 **textContent**, **새로운 요소의 추가 또는 삭제**시에는 **DOM 조작 방식을 사용***

# 이벤트 핸들링
참고 : [[[JS] 이벤트 루프(Event Loop)와 동시성(Concurrency)]]
![](https://i.imgur.com/xryTJyx.png)
## 대표적인 이벤트 종류
- load : 웹페이지의 로드가 완료되었을 때
- scroll : 사용자가 페이지를 위아래로 스크롤할 때
- keydown : 키를 누르고 있을 때
- keyup : 누르고 있던 키를 뗄 때
- keypress : 키를 누르고 뗏을 때
- click : 마우스 버튼을 클릭했을 때
- mouseover : 마우스를 요소 위로 움직였을 때 (터치스크린X)
- mouseout :마우스를 요소 밖으로 움직였을 때 (터치스크린X)
- focus :요소가 포커스를 얻었을 때
- blur :요소가 포커스를 잃었을 때
- input
	- input 또는 textarea 요소의 값이 변경되었을 때
	- contenteditable 어트리뷰트를 가진 요소의 값이 변경되었을 때
- change : select box, checkbox, radio button의 상태가 변경되었을 때
- submit : form을 submit할 때 (버튼 또는 키)
## 인라인 이벤트 핸들러 방식
- HTML 요소의 이벤트 핸들러 어트리뷰트에 이벤트 핸들러를 등록
- HTML과 Javascript는 관심사가 다르므로 분리하는것이 좋기 때문에, **더이상 사용되지 않는 방법**
- 여러 개의 문을 전달할 수 있음
```
<!DOCTYPE html>
<html>
<body>
  <button onclick="myHandler1(); myHandler2();">Click me</button>
  <script>
    function myHandler1() {
      alert('myHandler1');
    }
    function myHandler2() {
      alert('myHandler2');
    }
  </script>
</body>
</html>
```
- onclick과 같이 on으로 시작하는 이벤트 어트리뷰트의 값으로 함수 호출을 전달함
	- 이벤트 어트리뷰트의 값으로 전달한 함수 호출이 즉시 호출되는 것은 아님
	- 이벤트 어트리뷰트 키를 이름으로 갖는 함수를 암묵적으로 정의
	- 함수의 몸체에 이벤트 어트리뷰트의 값으로 전달한 함수 호출을 문으로 가짐
## 이벤트 핸들러 프로퍼티 방식
- 인라인 이벤트 핸들러 방식처럼 HTML과 Javascript가 뒤섞이는 문제는 해결할 수 있는 방식
- 단점 : 하지만 이벤트 핸들러 프로퍼티에 하나의 이벤트 핸들러만을 바인딩할 수 있음
```
<!DOCTYPE html>
<html>
<body>
  <button class="btn">Click me</button>
  <script>
    const btn = document.querySelector('.btn');

    // 이벤트 핸들러 프로퍼티 방식은 이벤트에 하나의 이벤트 핸들러만을 바인딩할 수 있다
    // 첫번째 바인딩된 이벤트 핸들러 => 실행되지 않는다.
    btn.onclick = function () {
      alert('① Button clicked 1');
    };

    // 두번째 바인딩된 이벤트 핸들러
    btn.onclick = function () {
      alert('① Button clicked 2');
    };

    // addEventListener 메소드 방식
    // 첫번째 바인딩된 이벤트 핸들러
    btn.addEventListener('click', function () {
      alert('② Button clicked 1');
    });

    // 두번째 바인딩된 이벤트 핸들러
    btn.addEventListener('click', function () {
      alert('② Button clicked 2');
    });
  </script>
</body>
</html>
```
## addEventListener 메소드 방식(IE 9 이상)
- IE 8 이하 -  `attachEvent` 메소드 사용
```
if (elem.addEventListener) {    // IE 9 ~
  elem.addEventListener('click', func);
} else if (elem.attachEvent) {  // ~ IE 8
  elem.attachEvent('onclick', func);
}
```
- `addEventListener` 메소드를 이용하여 대상 DOM 요소에 이벤트를 바인딩하고 해당 이벤트가 발생했을 때 실행될 콜백 함수(이벤트 핸들러)를 지정

![](https://poiemaweb.com/img/event_listener.png)
- 장점
	- 하나의 이벤트에 대해 하나 이상의 이벤트 핸들러를 추가할 수 있음
	- 캡처링과 버블링을 지원
	- HTML 요소뿐만아니라 모든 DOM 요소(HTML, XML, SVG)에 대해 동작(브라우저는 웹 문서(HTML, XML, SVG)를 로드한 후, 파싱하여 DOM을 생성)
- addEventListener 메소드에서 지정한 이벤트 핸들러는 콜백 함수
	- 이벤트 핸들러 내부의 **this**는 이벤트 리스너에 바인딩된 요소(currentTarget)를 가리킴(이벤트 객체의 currentTarget 프로퍼티와 같음).
```
function foo() {
  alert('clicked!');
}
// elem.addEventListener('click', foo()); // 이벤트 발생 시까지 대기하지 않고 바로 실행된다
elem.addEventListener('click', foo);      // 이벤트 발생 시까지 대기한다
```

```
<!DOCTYPE html>
<html>
<body>
  <label>User name <input type='text'></label>
  <em class="message"></em>

  <script>
    const MIN_USER_NAME_LENGTH = 2; // 이름 최소 길이

    const input = document.querySelector('input[type=text]');
    const msg = document.querySelector('.message');

    function checkUserNameLength(n) {
      if (input.value.length < n) {
        msg.innerHTML = '이름은 ' + n + '자 이상이어야 합니다';
      } else {
        msg.innerHTML = '';
      }
    }

    input.addEventListener('blur', function () {
      // 이벤트 핸들러 내부에서 함수를 호출하면서 인수를 전달한다.
      checkUserNameLength(MIN_USER_NAME_LENGTH);
    });

    // 이벤트 핸들러 프로퍼티 방식도 동일한 방식으로 인수를 전달할 수 있다.
    // input.onblur = function () {
    //   // 이벤트 핸들러 내부에서 함수를 호출하면서 인수를 전달한다.
    //   checkUserNameLength(MIN_USER_NAME_LENGTH);
    // };
  </script>
</body>
</html>
```
# JS - CSS 제어
- 객체.style.속성명 = "속성값"
- **.style** 규칙 : **CSS에 "-"가 있는 경우** 카멜케이스 적용
```
//getElementsByClassName
document.getElementsByClassName("class")[0].style.borderColor = "red";

//getElementById
document.getElementById("id").style.borderColor = "red";

//querySelector
document.querySelector(".class").style.borderColor = "red";
```

# JS - class 제어
## 클래스 변경
- 객체.style.className = "클래스명1 클래스명2"
```
getElementsByClassName
document.getElementsByClassName("class")[0].className = "active";

getElementById
document.getElementById("id").className = "active";

querySelector
document.querySelector(".class").className = "active";


// 활용
let elm = document.getElementById('id'); 

if(elm.className === 'active'){ 
	elm.className = 'inactive'; 
} else { 
	elm.className = 'active'; 
};
```
## 클래스 제어
-  객체.style.classList.메소드('클래스명')
	- add : 클래스 추가
	- remove : 클래스 제거
	- toggle : 토글
	- replace : 대체

---
# 오늘의 멘토링 🥸
- Q1-1 : `[YANA]`지난 11월 23일에 Spring Boot 3.2가 정식 릴리즈 되면서 생긴 궁금증입니다..!멘토님께서 보시기에, 현 상황에서 첫 스프링 프로젝트를 진행할 신입 개발자가 새로운 팀 프로젝트를 진행한다면가장 최근 릴리즈 버전인 3.2버전을 사용하는것을 추천하시는지, 아니면 조금 더 안정화되고 레퍼런스가 많은 3.0 혹은 3.1 버전을 추천하시는지 궁금합니다..!
	- A : 내가 개발을 한다고 하면, 나는 새로운 이슈를 마주하는것을 즐기기 때문에 3.2버전을 쓸 것 같다. 하지만 신입과 주니어 개발자라는 대상이라고 하면 레퍼런스가 많은 3.0버전을 사용하라고 할 것 같다. 어느정도 경력이 있는 개발자라면 모르겠지만, 경력이 없는 개발자에게 문제가 발생했을 때 구글링으로 해결이 되지 않는다는것은 꽤나 큰 장벽일수 있기 때문이다.
- Q1-2 : `[YANA]`저같은 경우엔 사실 최근에 rest-client를 사용하기 위해 3.2버전을 사용중에있는데요, 만약 버전 이슈가 의심되는 상황이 발생할 경우에는 어떤식으로 풀어가는게 좋을까요?
	- A : 오픈소스를 직접 뜯어보고 의심되는 부분을 명확하게 해서 해결방법을 해당 오픈소스 라이브러리에 pull request 해보는 방법과, maintainer에게 문의를 남기는 방법이 있다. 전자의 경우에는 코드를 풀어가는 방법이나 여타 경우로 거부되는 경우도 많지만, 해당 요청을 해보는 것 만으로도 좋은 경험이 될 것 같다.
- Q1-3 : `[YANA]`아무래도 주니어 개발자이다보니, 사실 버전이슈인지 아닌지 판단조차 되지 않는 경우가 있는데, 해당 경우에 spring boot 버전을 낮춰보고 테스트를 해봤을 때 문제없이 동작한다면 버전이슈라고 판단하는 방법도 괜찮을까요?
	- A : 주니어 입장에서 그런 방법도 나쁘지는 않다. 하지만 가능하다고 하면 오픈소스를 뜯어보고자 하는 개발자가 동료가 되는게 더 기쁠 것 같다.
- Q2-1 : `[YANA]`spring boot 어플리케이션에서 dto를 사용 할 때 어플리케이션 개발 초기에는 컨트롤러와 서비스 레이어 각각 나눠서 두기에는 두 dto간 요소 차이가 없을것이고 결국에는 코드의 중복으로 이어지기에, 대부분의 개발 초반에는 하나의 dto로 개발을 진행한 뒤, 프로젝트 규모가 커지면 추후에 분리하는편이라고 들었습니다. 
  그렇다면, 멘토님께서는 두 레이어에서 dto를 분리해야하는 시기는 언제쯤이라고 보실까요..!
	- A : 각 레이어의 로직이 많이 복잡해지거나, 특화로직과 비동기 통신이 들어갈 때, 그리고 완전히 다른 entity가 필요하다고 판단이 들때 팀내의 논의를 통해 분리를 해야한다고 본다.
- Q2-2 : `[YANA]`비동기 통신을 적용할 때 dto를 분리해야한다고 하셨는데, 제가 아직 경험이 없어 잘 이해가 가지 않았습니다! 혹시 추가적으로 설명을 해주실 수 있을까요?
	- A : 비동기 통신의 예를 들자면, 의류쇼핑몰 도메인에서 결제 시스템에 토스결제를 도입하는 상황을 예로 든다. 해당 비동기 통신을 위해서는 첫째로 토스가 원하는 request -dto로 전달하는것이 필요할 것이며, 토스에 요청을 한 뒤 클라이언트에 먼저 응답을 보내주던, ajax로 dto 응답을 보내주던 dto이 종류는 여러개가 될 수 있다. 
	  그리고 이런 3자 호출에 대해서도 사용자에게 응답을 내려 줄 떄, 해당 요청을 받은 직후 보내는 dto, 3자 호출 request를 보내는 시점의 dto, 3자호출 요청완료후 dto처럼 dto가 여러개가 생긴다. 보통 현업에서 이러한 3자호출 dto군을 어떻게 이름을 짓고 관리할건지 팀내에서 많은 논의를 한다.
- Q2-3 : `[YANA]`비동기 통신 관련해서 설명해주신 내용을 제 현 상황에 적용해보면, 이미지 업로드 request(file)를 받았을때 즉시 내려줄 response dto, s3업로드를 시도하기 시작하면서 내려줄 response dto, s3업로드 실패시 재시도를 하면서 내려줄 response dto, s3업로드 완료 후 내려줄 response dto를 각각 분리한다는 관점으로 보면 될까요?
	- 그렇다. 특히 해당 응답들을 클라이언트에 내려줄때 요새는 폴링 혹은 웹소켓 경로를 열어놓는 방법이 현대 트랜드에 있다. 
- Q2-4 : `[YANA]`관련해서 해당 프로젝트의 경우 카프카를 도입할 예정에 있는데, 카프카를 활용해 응답을 보내주는 방법도 검토할 수 있을까요?
	- A : 가능하다. 혹시 카프카가 무엇이라고 생각하나?
- Q2-5 : `[YANA]`아직은 이론만 훝어보고 실제로 운영을 해본 경험은 없어 명확히 어떤것이다라고 말하기는 조심스럽지만, 제가 이해한 바로는 메시지 브로커이면서 분산처리를 지원하는 기술이라고 생각합니다. 메시지들을 분산처리함으로써 유실되는 데이터가 없도록 하는데에 사용되어 '반드시 한 번'처리와 여러 설정을 통해 '정확히 한번'까지 지원하는 플랫폼이라고 이해하고 있습니다.
	- A : 그렇다. 카프카는 범용 메시지브로커이다. 따라서 위와같은 경우에도 활용 할 수 있다. 하지만 보통 클라이언트에서 카프카를 직접 구독하도록 하지 않는다. 보통 웹소켓을 열어주거나 grpc나 서버샌드이벤트를 이용하는 편이다.
- Q2-6 : `[YANA]`마지막으로 dto를 각각의 경우에 맞춰서 만들어주는게 맞다고 본다고 말씀하셔서 생긴 궁금증입니다. 최근 innerClass를 통해 dto를 생성해주는 트렌드도 있던데 멘토님께서는 이러한 방법에 대해서는 어떻게 생각하시나요?
	 - A : 내부통신용은 innerClass 사용해도 좋다고 본다. 하지만 외부통신은 적합하지 않다고 생각한다. 

## 오늘 멘토링과 관련해서 생각/공부해봐야 할 주제 🤔
1. 진행중인 프로젝트 **3자 호출 DTO의 명명**방법을 어떻게 할 지 고민해보자
3. **클라이언트**에서 **카프카를 직접 구독하도록 하지 않는** 이유는 뭘까?
4. 왜 **외부통신**에서는 innerClass 방식보다 **각각의 dto를 만들어** 주는 편이 낫다고 하셨을까? 
	- innerClass 사용시 하나의 엔티티에 대한 CRUD용 dto를 하나의 파일과 클래스에서 다룰 수 있다는 점이 좋았는데, 외부 통신의 경우에는 내부 api처럼 CRUD를 하는게 아니라 요청과 응답이 주류라서 응집시키는것보다 명명을 명확하게 하는편이 나아서 그러나?
5. DTO 관련해서 **innerClass** 방식과 **java 14이후의 record** 방식을 비교해보는것도 재밌겠다.
	- innerClass 사용시 하나의 엔티티에 대한 CRUD용 dto를 하나의 파일과 클래스에서 다룰 수 있다는 점이 좋았는데, record와 동시에 사용하기에는 어려워 보인다.. 그렇다면 응집시킬 dto에 대해서는 innerClas방식을 사용하고, 응집시키지 않을 dto나 복잡한 로직을 가진 dto에 대해서는 record를 사용하는게 좋으려나? 두가지 방법 장단점에 대해서 생각을 정리 해봐야겠다.
6. 클라이언트에 **비동기 통신의 응답을 내려줄 방법**으로 여러가지 방법이 있는 것 같은데 어떤 방법을 사용할까?
	- **websocket** 열어주기(채팅 서비스를 위해 적용 예정이기 때문에 좋을것 같기도)
	- **gRPC(google Remote Procedure Call)**..?뭐야이거
	- **Server-Sent Events (SSE)**..?넌또뭐야
	- **Long Polling** : 응답을 지연시키기..? 대체 넌또뭐고
	- 추가 검색 : **HTTP/2 Server Push** - 클라이언트를 판별할수있는 방법이 뭐지?
	  참고 : [WebSockets vs SSEs vs gRPC vs Polling vs Webhooks : Efficient Real-Time Communication](https://medium.com/@wadkararyan01/efficient-real-time-communication-and-crud-operations-c8f35283ce38)

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 