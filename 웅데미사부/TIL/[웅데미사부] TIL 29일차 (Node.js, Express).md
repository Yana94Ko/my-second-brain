---
tistoryBlogName: yanacoding
tistoryTitle: "[웅데미사부] TIL 29일차 (Node.js, Express)"
tistoryTags: " 유데미,유데미큐레이션,유데미취업부트캠프,유데미부트캠프,프론트엔드,백엔드,개발부트캠프"
tistoryVisibility: "3"
tistoryCategory: "1197249"
tistorySkipModal: true
tistoryPostId: "278"
tistoryPostUrl: https://yanacoding.tistory.com/278
---
오늘 수강한 강의 : [【한글자막】 완전 초보자를 위한 Java 프로그래밍 : 단기간에 Java 완벽 정복](https://www.udemy.com/course/best-java-programming/)

---
# 오늘의 강의 정리 📗
## Express.js
Express.js는 Node.js를 위한 간편하고 유연한 웹 애플리케이션 프레임워크로, 웹 및 모바일 애플리케이션을 빠르게 개발할 수 있도록 도와줌. Express.js는 빠르고 간단한 웹 애플리케이션을 구축하기 위한 강력한 도구이며, Node.js의 생태계에서 많은 개발자들에게 선호되고 사용되고 있음

### 주요 특징:
1. **미들웨어 지원:**
   - Express.js는 미들웨어를 지원하여 요청과 응답 사이에 여러 작업을 수행할 수 있습니다. 미들웨어는 `app.use()` 메서드를 통해 추가되며, 요청 처리 파이프라인을 구성할 수 있습니다.
2. **라우팅:**
   - Express는 HTTP 메서드와 URL 패턴에 기반하여 라우팅을 정의할 수 있습니다. `app.get()`, `app.post()` 등의 메서드를 사용하여 각각의 라우트에 대한 핸들러를 등록할 수 있습니다.
3. **템플릿 엔진 지원:**
   - Express는 여러 템플릿 엔진을 지원하여 동적인 HTML 생성이 가능합니다. 대표적으로 Pug, EJS, Handlebars 등이 있습니다.
4. **정적 파일 서비스:**
   - `express.static` 미들웨어를 사용하여 정적 파일 (이미지, CSS, JavaScript 등)을 쉽게 서비스할 수 있습니다.
5. **HTTP 유틸리티 메서드:**
   - `res.send()`, `res.json()`, `res.render()` 등의 메서드를 통해 간단하게 HTTP 응답을 생성할 수 있습니다.
6. **모듈화:**
   - Express.js는 모듈화가 용이하며, 필요한 기능을 라이브러리 형태로 추가할 수 있습니다.

### 기본 사용법
1. **설치:**
   ```bash
   npm install express
   ```

2. **기본 애플리케이션 생성:**
   ```javascript
   const express = require('express');
   const app = express();

   app.get('/', (req, res) => {
       res.send('Hello, Express!');
   });

   app.listen(3000, () => {
       console.log('Server is running on port 3000');
   });
   ```

3. **라우팅 및 미들웨어 사용:**
   ```javascript
   const express = require('express');
   const app = express();

   // 미들웨어 등록
   app.use((req, res, next) => {
       console.log('Middleware executed');
       next(); // 다음 미들웨어로 제어를 전달
   });

   // 라우트 핸들러
   app.get('/', (req, res) => {
       res.send('Hello, Express!');
   });

   app.listen(3000, () => {
       console.log('Server is running on port 3000');
   });
   ```

### Middleware in Express.js
- **목적:**
  - Express에서 HTTP 요청 및 응답 객체에 대한 중간 처리 로직을 구현하는 데 사용된다.
- **특징:**
  - 미들웨어는 함수의 체인으로 구성되며, 순서대로 실행된다.
  - 요청과 응답 객체에 변형을 가하거나, 다음 미들웨어 함수로 제어를 전달할 수 있다.
- **사용 방법:**
  - `app.use()` 메서드를 사용하여 미들웨어를 등록한다.
  - 또는 특정 경로에만 미들웨어를 적용하려면 `app.use('/path', middleware)`와 같이 경로를 지정할 수 있다.
- **예시:**
  ```javascript
  const express = require('express');
  const app = express();

  // 미들웨어 등록
  app.use((req, res, next) => {
      console.log('Middleware executed');
      next(); // 다음 미들웨어로 제어를 전달
  });

  // 라우트 핸들러
  app.get('/', (req, res) => {
      res.send('Hello, World!');
  });

  // 서버 시작
  app.listen(3000, () => {
      console.log('Server is running on port 3000');
  });
  ```

### Router in Express.js
- **목적:**
  - Express에서 라우트를 그룹화하고 모듈화하여 라우트 핸들러를 구성하는 데 사용된다.
- **특징:**
  - 라우터는 독립적으로 사용될 수도 있고, 다른 라우터에 중첩하여 사용될 수도 있다.
  - 라우터 객체는 미들웨어처럼 동작하며, `app.use()`로 등록할 수 있다.
- **사용 방법:**
  - `express.Router()`를 사용하여 라우터 객체를 생성하고, 해당 객체에 라우트 핸들러를 등록한다.
  - 이후에 `app.use('/prefix', router)`와 같이 경로를 지정하여 앱에 등록한다.
- **예시:**
  ```javascript
  const express = require('express');
  const app = express();
  const router = express.Router();

  // 라우트 핸들러 등록
  router.get('/', (req, res) => {
      res.send('Router Home');
  });

  router.get('/about', (req, res) => {
      res.send('Router About');
  });

  // 앱에 라우터 등록
  app.use('/prefix', router);

  // 서버 시작
  app.listen(3000, () => {
      console.log('Server is running on port 3000');
  });
  ```

### Express and MVC
- **Express와 MVC:**
  - Express는 웹 애플리케이션을 개발하기 위한 웹 프레임워크이며, MVC (Model-View-Controller) 아키텍처를 따르는데 이는 다음과 같이 구성된다.
    - **Model:** 데이터와 데이터 로직을 처리하는 부분.
    - **View:** 사용자에게 보여지는 화면을 담당하는 부분.
    - **Controller:** 사용자의 입력을 받아 Model과 View를 조작하는 부분.
  - Express에서는 라우트 핸들러 함수가 컨트롤러 역할을 수행하며, 뷰 역할은 클라이언트 사이드에서 처리된다.
  - 데이터베이스와의 상호 작용은 모델로 추상화되어야 하며, 필요에 따라 ORM 또는 ODM을 사용할 수 있다.
  - 뷰 엔진을 사용하면 서버 측에서도 뷰를 렌더링할 수 있다.

- **예시:**
  ```javascript
  // Controller (라우트 핸들러 함수)
  const express = require('express');
  const app = express();

  app.get('/home', (req, res) => {
      // 모델과 상호 작용
      const data = fetchDataFromDatabase();

      // 뷰 렌더링
      res.render('home', { data });
  });

  // 서버 시작
  app.listen(3000, () => {
      console.log('Server is running on port 3000');
  });
  ```
  - 위의 예시에서 `/home` 경로에 대한 라우트 핸들러 함수가 컨트롤러 역할을 하며, 모델에서 데이터를 가져와 뷰에 렌더링하는 역할을 수행한다.
Express.js와 Pug는 웹 애플리케이션 개발에서 함께 사용되는 조합입니다. Express.js는 Node.js 기반의 웹 프레임워크이고, Pug는 템플릿 엔진 중 하나입니다. 함께 사용되면 동적인 웹 페이지를 효과적으로 구성할 수 있습니다.

### Express.js와 Pug 
Express.js에서 Pug를 사용하면, HTML 코드를 간결하게 작성할 수 있고, 동적 데이터를 템플릿에서 효과적으로 사용할 수 있음. Pug를 통해 HTML 대신에 들여쓰기를 사용하여 템플릿을 작성할 수 있음

1. **Express.js 설치:**
   ```bash
   npm install express
   ```

2. **Pug 설치:**
   ```bash
   npm install pug
   ```

3. **Express.js 애플리케이션에서 Pug 설정:**
   ```javascript
   const express = require('express');
   const app = express();
   const port = 3000;

   // Pug를 뷰 엔진으로 설정
   app.set('view engine', 'pug');

   // Pug 템플릿이 있는 디렉토리 설정 (기본값은 views 디렉토리)
   app.set('views', './views');

   // 라우트 핸들러
   app.get('/', (req, res) => {
       res.render('index', { title: 'Express with Pug' });
   });

   // 서버 시작
   app.listen(port, () => {
       console.log(`Server is running on port ${port}`);
   });
   ```

4. **Pug 템플릿 작성 (`views/index.pug`):**
   ```pug
   html
     head
       title= title
     body
       h1 #{title}
   ```

5. **서버 실행:**
   ```bash
   node your_app_file.js
   ```

6. **웹 브라우저에서 확인:**
   - http://localhost:3000 으로 접속하여 Pug 템플릿이 렌더링된 웹 페이지 확인

---
`*` 유데미(Udemy) 큐레이션을 받고싶다면? : [https://bit.ly/43JLW2l](https://bit.ly/43JLW2l) 

`*` STARTERS 취업 부트캠프 공식 블로그 : [https://blog.naver.com/udemy-wjtb](https://blog.naver.com/udemy-wjtb) 

본 후기는 유데미 취업부트캠프 프론트엔드&백엔드 리뷰로 작성되었습니다. 