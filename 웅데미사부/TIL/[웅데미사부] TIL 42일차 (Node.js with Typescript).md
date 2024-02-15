## `[강의전]` 사전 지식 한 입
### Server의 정의
"요청에 대해 응답을 보내주는 것"

### Node.js 란
- "자바스크립트 런타임 환경, V8, Event-driven"
- 특징 : Single-thread, Event-driven, Non-Blocking I/O, Event loop

> [!info] [Node.js](https://nodejs.org/en/about)
> As an asynchronous event-driven JavaScript runtime, Node.js is designed to build scalable network applications. In the following "hello world" example, many connections can be handled concurrently. Upon each connection, the callback is fired, but if there is no work to be done, Node.js will sleep.
> This is in contrast to today's more common concurrency model, in which OS threads are employed. Thread-based networking is relatively inefficient and very difficult to use. Furthermore, users of Node.js are free from worries of dead-locking the process, since there are no locks. Almost no function in Node.js directly performs I/O, so the process never blocks except when the I/O is performed using synchronous methods of Node.js standard library. Because nothing blocks, scalable systems are very reasonable to develop in Node.js.

``` js
const http = require('node:http');
const hostname = '127.0.0.1';
const port = 3000;
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});
server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

Node.js 란, 확장 가능한 웹 애플리케이션을 만들기 위한 비동기 이벤트기반 자바스크립트 런타임 환경을 말한다. 이는 OS에서 많이 사용되는 스레드를 이용한 동시성 모델들과는 조금 다르다. 스레드를 활용한 모델들은 상대적으로 비효율적이며, 사용하기 어렵다.
Node.js는 lock이 없기 때문에 프로세스 교착상태에 대한 걱정이 없다. 이는 Non-Blocking I/O라는 Node.js의 특징과도 관련되어있다.
### Express란?

> [!info]  [Express](https://expressjs.com/)
> Fast, unopinionated, minimalist web framework for Node.js.
> Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications


#### festify와의 차이점
- Express는  비교적 


## 오늘의 강의 정리 📗


---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 
유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프