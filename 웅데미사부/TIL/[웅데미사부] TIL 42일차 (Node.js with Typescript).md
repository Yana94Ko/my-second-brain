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



데브옵스란 무엇인가?
개발문화와 프로세스에 대한 고민
플랫폼 개발 팀장님

북클럽 스마트씽크빅 스마트올 투게더

클라우드플랫폼 최적화

유데미 플랫폼 운영 AWS 클라우드 운영관리, 효율적인지 여부 연구

개발 표준

형상관리 CICD 

클라우드 현대화 검토

개발자 놓치지마 최신기술 검토 분석 파일럿

교육출판회사-> 에듀테크 회사로 정착

"어린이의 10년후를 생각하는 기업" 

10년 후를 생각하면서 공감자를 가지고 협업해서 움직임

매일 1억건 이상의 독서 학습데이터를 수집 분석

에듀테크 연구소에서 만든 ar 독서제품
웅진 인터랙티브북 + 겨육+ 증강현실

총 180인의 기획 디자이너 퍼블리셔 DBA FE/BE

빅데이터 AI, 비대면 학습, 학습에 대한 미래

오픈 플랫폼 - 양질의 데이터 쉐어 고민

북클럽 확장 고민

글로벌 확장 고민

에듀테크연구소 4층


-----
엔지니어 vs 개발자

코드치는 원숭이가 되지 말자... => 알고리즘을 다지자

---
개발환경 및 도구

인텔리제이
지라(플로우)
컨플루언스

노션 - 워드

젠킨스 깃랩 70% SVN 30%


디비버 EXERD다이어그램 작성시 HeidiSQL => ...?

XSHELL7 mobax 파일지라 푸티... =>..? 로그 확인할때../? 리눅스사용즁


이클립스 인텔리 / VScode, 인소노미아  editPlus 

자바 노드 파이썬 리액트
swagger, postman

톰캣 스프링
jmeter - 성능테스트

nginx

파이썬 장고

스카우터(모니터링)
+그라파나


---
로깅 아키텍처

AWS EFS -> aggregate->  promtai(pluemtid?) -Send -> grafana loki - -> grapana 

서비스, 로그 적재 -> 수집기 -> 데이터 저장소 -> 모니터링 ㅐㄷ시보드


성증, 자원 사용료
Node exporter -> 프로메테우스 -> 그라파나
JMX 활용 어플리케이션 상태 전송
Acuator 활용 어플리케이션 상태 정보 -> 프로메테우스(pull) -> 그라파나

---
배포 프로세스

vonfigure checkout (git, svn) => jenkins(변화 모니터링 - > 신규 데이터 폴링 - > 체크업 -> 빌드) => 도터 컨테이너 -> AWS ECR -> push _> deploy -> 쿠버네티스 pull_

---
도커 서비스 환경

배포전략 :
롤링 - 사용자가 적을 때
블루그린 - 돈이 많이 듦 로드밸런식
카나리 -> 쿠버네티스

쿠버네티스 istio 로 사용해야만 카나리 배포가 가능하다







## 오늘의 강의 정리 📗


---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 
유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프