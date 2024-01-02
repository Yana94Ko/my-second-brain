---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 12일차 (React, 리액트)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "238"
tistoryPostUrl: https://yanacoding.tistory.com/238
---

오늘 수강한 강의 : [# 【한글자막】 React 완벽 가이드 with Redux, Next.js, TypeScript](https://www.udemy.com/course/best-react/?utm_source=adwords&utm_medium=udemyads&utm_campaign=Webindex_Catchall_la.KR_cc.KR&utm_term=_._ag_154831691911_._ad_667917181863_._kw__._de_c_._dm__._pl__._ti_dsa-1456167871416_._li_1009871_._pd__._&matchtype=&gad_source=1&gclid=Cj0KCQiAv8SsBhC7ARIsALIkVT0YQL1Z1xCLn5v8iq06aTV-vGZOOgmozcCu1fIQne3Vm82noB_KqDQaAp61EALw_wcB)

---
# 오늘의 강의 정리 📗
<목차여기>
# Component 
- 커스텀 컴포넌트는 사용되는 시점에 반드시 대문자로 시작해야 한다.
	- 리액트는 기본적으로 소문자이면 디폴트로 존재하는 컴포넌트(ex. div 등)를 해당 이름으로 조회하기 때문.
- root element(<> ... </>)는 반드시 하나만 존재해야 하고, default 컴포넌트여야 함
- 컴포넌트를 여러 개 쓰려면 반드시 root element로 감싸서 사용
```jsx
/* Greeting이라는 이름의 컴포넌트 */

function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

export default function App() {
  return (
    <>
      <Greeting name="Sara" />
      <Greeting name="Cahal" />
      <Greeting name="Edite" />
    </>
  );
}
```
# props
- 상위 컴포넌트가 하위 컴포넌트에 값을 전달할때 사용(단방향 데이터 흐름)
- 수정할 수 없다(자식입장에선 읽기 전용인 데이터)
- 함수의 매개변수와 비슷한 역할
- HTML 요소의 속성을 가지고 오는 문법과 동일
```jsx
function Post(props) {
  return (
    <li className={classes.post}>
      <p className={classes.author}>{props.author}</p>
      <p className={classes.text}>{props.body}</p>
    </li>
  );
}
```
# State
- `props`는 (함수 매개변수처럼) 컴포넌트_에_ 전달되는 반면 `state`는 (함수 내에 선언된 변수처럼) 컴포넌트 _안에서_ 관리
- 컴포넌츠 내에서 변경되는 값을 관리해야 할 때 사용
## [setState](https://ko.legacy.reactjs.org/docs/faq-state.html)
```jsx
function addPostHandler(postData) {
  setPosts((existingPosts) => [postData, ...existingPosts]);
}
```
## [useState](https://react.dev/reference/react/useState)
## [state lifting](https://ko.legacy.reactjs.org/docs/lifting-state-up.html)
## state를 활용한 조건부 컨텐츠 로딩
```jsx
  function submitHandler(event) {
    event.preventDefault();
    const postData = {
      body: enteredBody,
      author: enteredAuthor
    };
    onAddPost(postData);
    onCancel();
  }

  return (
    <form className={classes.form} onSubmit={submitHandler}>
      <p>
        <label htmlFor="body">Text</label>
        <textarea id="body" required rows={3} onChange={bodyChangeHandler} />
      </p>

      <p>
        <label htmlFor="name">Your name</label>
        <input type="text" id="name" required onChange={authorChangeHandler} />
      </p>
      /*********************************/
      <p className={classes.actions}>
        <button type="button" onClick={onCancel}>
          Cancel
        </button>
        <button>Submit</button>
      </p>
      /*********************************/
    </form>
  );
}
```
# useEffect
- 컴포넌트가 렌더링 될 때 특정 작업을 실행할 수 있도록 하는 Hook
	- 클래스형 컴포넌트에서는 생명주기 메소드를 사용할 수 있었는데, 이를 함수형 컴포넌트에서도 사용할 수 있게 된 것
	- 라이프사이클 훅을 대체할 수 있게 됨
# Routing
-  페이지 간 navigating을 구현할 수 있도록 다양한 기능들이 제공
- RouterProvider, createBrowserRouter, 상대경로를 이용한 path 표현(..) 등
![(출처: 유데미 React 완벽 가이드 with Redux, Next.js, TypeScript)](https://i.imgur.com/oY3qWHl.png)
# 레이아웃 라우트(Layout Route)
- 여러 페이지에 레이아웃으로 적용될 컴포넌트를 특정 route로 지정
- 적용 받을 페이지들은 레이아웃 라우트의 children
# 동적 라우트(dynamic route)
- path가 동적으로 결정되는 라우팀
# Link
- a 태그를 사용할 시 매번 페이지가 재 렌더링 되면서 전역 state가 모두 날아감
- 이를 해결하기 위한 방식으로 Link 컴포넌트 사용
# loader()
- useEffect보다 더 편리하게 데이터를 가져올 수 있는 기능
# action()
- 데이터를 전송하는 작업을 더 편리하게 할 수 있는 기능
- Form으로 HTML의 기본제공 태그인 form을 대체
# CSS 모듈로 CSS 스타일 적용
```jsx
import classes from "./Post.module.css";

function Post({ author, body }) {
  return (
    <li className={classes.post}>
      <p className={classes.author}>{author}</p>
      <p className={classes.text}>{body}</p>
    </li>
  );
}

export default Post;
```

```css
.post {
  margin: 1rem 0;
  padding: 1rem;
  background-color: #9c7eee;
  border-radius: 8px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.2);
  animation: animate-in 1s ease-out forwards;
}

.author {
  font-size: 0.8rem;
  font-weight: bold;
  color: #543280;
  margin: 0;
  text-transform: uppercase;
}

.text {
  white-space: pre-wrap;
  font-size: 1.25rem;
  margin: 0.25rem 0 0 0;
  color: #593884;
  font-style: italic;
}

@keyframes animate-in {
  from {
    opacity: 0;
    transform: translateY(1rem);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
```
#  특별한 "children" 프로퍼티
- children: A 컴포넌트 사이에 B 컴포넌트가 있을 때, A 컴포넌트에서 B 컴포넌트 내용을 보여주려고 사용하는 props


---
# 오늘의 멘토링 🥸
- Q1 : 개발자 분들중에서 Notion이나 Obsidian github 블로그 등의 툴과 플랫폼을 활용해서 본인만의 지식을 관리하고 second brain화 하는 분들을 많이 봐왔습니다..! 저는 처음에는 블로그를 써오다가, 어떤 생각이 떠올랐을때 마음먹지 않고 빠르게 기록해놓을수 있는 Notion으로 툴을 바꾸었다가. 최근에는 노션이 반응이 너무느려져서 Obsidian으로 옮겨온 유목민인데요..! **기록 유목민으로써, 강사님은 어떤 툴을 사용하시는지 궁금합니다..!**
	- A : 에버노트, google worksheet, Notion을 사용하다가 최근에는 obsidian으로 옮겨온지 6개월정도 되어간다. 앞으로도 또 옮겨가게 되더라도 obsidian 처럼 개인 커스텀을 할 수 있고, 오프라인에서 돌아가는 노트 툴을 사용할것같다.
- Q2 : 혹시 멘토님이 추천하시는 옵시디언 플러그인이 있을까요?
	- A : Advanced Tables, Banners, Book Search, Caelendar, Chronology, Custom Attachment Location, Day Planner, [Diagrams.net](http://diagrams.net/), Enhancing Mindmap, Excalidraw, Game Search, Iconize, Kanban, Media DB Plugin, Mermaid Tools, Mind Map, Outliner, PlantUML, ReaditLater, Reminder, Tag Wrangler, Tasks, Tasks Calendar, Wrapper, Templater

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 