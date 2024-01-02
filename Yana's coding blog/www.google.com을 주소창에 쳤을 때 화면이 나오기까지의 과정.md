---
tistoryBlogName: yanacoding
tistoryTitle: www.google.com을 주소창에 쳤을 때 화면이 나오기까지의 과정
tistoryTags: web,DNS,IP,TCP,로드밸런서,L4,L7
tistoryVisibility: "0"
tistoryCategory: "1155358"
tistorySkipModal: true
tistoryPostId: "241"
tistoryPostUrl: https://yanacoding.tistory.com/241
---
# www.google.com을 주소창에 쳤을 때 화면이 나오기까지의 과정

---

![](https://i.imgur.com/fJtx4Pp.png)

## 브라우저에서 www.google.com을 주소창에 입력하면

1. 우선 캐시에서 해당 DNS 주소를 검색해본다
    1. 만약 해당하는 주소가 있다면 검색된 ip 를 기반으로 통신을 시작한다
    2. 만약 해당 주소가 없다면 DNS 서버로 요청을 보내 해당하는 ip주소를 받는다
2. ip주소를 알아냈다면 TCP 통신을 통해 해당 ip 서버에 요청을 보낸다.
    1. 로드밸런서가 해당 요청을 받아, 해당하는 서버로 요청을 분산한다
    2. 해당하는 서버는 일련의 처리과정을 거쳐 응답메세지를 만든다.
    3. 만들어진 응답 메세지를 TCP 통신을 통해 다시 클라이언트에게 전송한다.
3. 브라우저는 받은 응답 메세지를 HTTP프로토콜을 사용하여 웹페이지를 구성하여 화면을 렌더링 한다.

## 브라우저에서 www.google.com을 주소창에 입력하면

1. www.google.com에 해당하는 IP주소가 브라우저에 캐시되었는지 확인한다.
    1. 캐시된 IP 주소가 있는 경우, 해당 IP 주소를 사용한다.
    2. 캐시된 IP 주소가 없는 경우, DNS 서버로 요청하여 IP 주소를 확인한다.
2. 응답받은 IP 주소로 TCP 커넥션을 맺고, HTTP 요청을 전송한다.
3. [www.google.com](http://www.google.com/) 서버의 로드밸런서는 수신된 HTTP 요청을 웹서버로 로드밸런싱한다.
    1. L4 로드밸런서인 경우, Round-Robin 또는 Least Connection 등 로드밸런싱 알고리즘을 통해서 부하 분산을 수행할 수 있다.
    2. L7 로드밸런서인 경우, L4의 부하분산 알고리즘도 가능하지만 추가적으로 HTTP 헤더(Cookie, Host 등)를 기반으로 부하 분산을 수행할 수 있다. (하지만 리소스를 좀 더 소모하므로 비용은 더 비쌀 수 있다)
4. 웹 서버는 응답을 전송한다.
5. 브라우저는 수신된 응답을 통해 웹페이지를 렌더링한다.

![](https://i.imgur.com/jRW7Pbs.png)
![](https://i.imgur.com/zWtmuHy.png)
![](https://i.imgur.com/iINTVZD.png)

## 참고자료

[https://aws.amazon.com/ko/blogs/korea/what-happens-when-you-type-a-url-into-your-browser/](https://aws.amazon.com/ko/blogs/korea/what-happens-when-you-type-a-url-into-your-browser/)