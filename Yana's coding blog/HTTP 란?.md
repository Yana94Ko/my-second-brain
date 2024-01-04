---
tistoryBlogName: yanacoding
tistoryTitle: HTTP 란?
tistoryTags: HTTP,HTTP request,HTTP respnes,message,HTTPS,QUID
tistoryVisibility: "3"
tistoryCategory: "1155358"
tistorySkipModal: true
tistoryPostId: "240"
tistoryPostUrl: https://yanacoding.tistory.com/240
---
# HTTP(Hyper Text Transfer Protocol)**란?

 > 📌 인터넷에서 HTML 문서와 같은 데이터를 주고받을 수 있도록 해주는 프로토콜.
 > 	애플리케이션 계층으로, 웹 서비스 통신에 사용.
 
- 즉, 웹상에서 네트워크로 서버끼리 통신을 할때 어떠한 형식으로 서로 통신을 하자고 규정해 놓은 "통신 형식" 혹은 "통신 구조" 라고 보면 됨
- TCP/IP 기반으로 되어있음
- HTTP 기본적으로 **request**(요청)/**response**(응답) 구조로 되어있음
    클라이언트가 HTTP request를 서버에 보내면 서버는 HTTP response를 보내는 구조  
    클라이언트와 서버 대부분의 통신이 요청과 응답으로 이루어 짐.

# [HTTP Response, Request 메시지의 구조(Start Line, Status Line, Header, Content)](https://developer.mozilla.org/ko/docs/Web/HTTP/Messages)
- HTTP 메시지는 서버와 클라이언트 간에 데이터가 교환되는 방식
- 요청('request')은 클라이언트가 서버로 전달해서 서버의 액션이 일어나게끔 하는 메시지
- 응답('response')은 요청에 대한 서버의 답변
- HTTP 요청과 응답의 구조
	1. 시작 줄('start-line')에는 실행되어야 할 요청, 또은 요청 수행에 대한 성공 또는 실패가 기록되어 있음. 
		- 이 줄은 항상 한 줄로 끝남
	2. 옵션으로 'HTTP 헤더' 세트가 들어감. 
		- 요청에 대한 설명, 혹은 메시지 본문에 대한 설명
	3. 요청에 대한 모든 메타 정보가 전송되었음을 알리는 빈 줄('blank line') 삽입
	4. 요청과 관련된 내용(HTML 폼 콘텐츠 등)이 옵션으로 들어가거나, 응답과 관련된 문서가 들어감. 
		- 본문의 존재 유무 및 크기는 첫 줄과 HTTP 헤더에 명시

![](https://i.imgur.com/lPTAmTr.png)

## HTTP Request Message
### HTTP Request Message 구조
HTTP Request Message는 공백(blank line)을 제외하고 3가지 부분으로 나누어짐
#### Start Line
- HTTP method
	-  '[HTTP 메서드](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods)'로, 영어 동사([`GET`](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods/GET), [`PUT`](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods/PUT),[`POST`](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods/POST)) 혹은 명사([`HEAD`](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods/HEAD), [`OPTIONS`](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods/OPTIONS))를 사용해 서버가 수행해야 할 동작을 나타냄
- Request target
	- HTTP Request가 전송되는 목표 주소
- HTTP version
	- HTTP version 명시(version에 따라 Request 메시지 구조나 데이터가 다를 수 있기 때문)
#### Headers
- request에 대한 추가 정보(addtional information)를 담고 있는 부분
- 크게 3가지 부분으로 나뉨(general headers, request headers, entity headers)
![](https://i.imgur.com/FrREBki.png)
- `Host` : 요청하려는 서버 호스트 이름과 포트번호
- `User-agent` : 클라이언트 프로그램 정보. 이 정보를 통해 서버는 클라이언트 프로그램(브라우저)에 맞는 최적의 데이터를 보내줄 수 있다.
- `Referer` : 바로 직전에 머물렀던 웹 링크 주소 
- `Accept` : 클라이언트가 처리 가능한 미디어 타입 종류 나열
- `If-Modified-Since` : 여기에 쓰여진 시간 이후로 변경된 리소스 취득. 페이지가 수정되었으면 최신 페이지로 교체한다.
- `Authorization` : 인증 토큰을 서버로 보낼 때 쓰이는 Header
- `Origin` : 서버로 Post 요청을 보낼 때 요청이 어느 주소에 시작되었는지 나타내는 값. 이 값으로 요청을 보낸 주소와 받는 주소가 다르면 CORS(Cross-Origin Resource Sharing) 에러가 발생한다.
- `Cookie` :  쿠키 값이 key-value로 표현
#### Body
- HTTP Request가 전송하는 데이터를 담고 있는 부분
- 전송하는 데이터가 없다면 body 부분은 비어있음
- post 요청일 경우, HTML 폼 데이터가 포함되어 있음
``` http
POST /test HTTP/1.1

Accept: application/json
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 83
Content-Type: application/json
Host: google.com
User-Agent: HTTPie/0.9.3

{
    "test_id": "tmp_1234567",
    "order_id": "8237352"
}
```

## HTTP Response Message

### HTTP Response Message 구조
- HTTP Response Message는 request와 동일하게 공백(blank line)을 제외하고 3가지 부분으로 나누어짐
#### Status Line
- HTTP Response의 상태를 간략하게 나타냄
- HTTP version
	- HTTP version명시(버전에 따른 메시지 형식이 다를 수 있기 때문)
- Status Code
	- HTTP status code를 명시(200, 404, 503.,)
- Status Text
	- HTTP status Text를 명시(OK, NOT FOUND, bad gateway)
#### Headers
- Request의 headers와 동일
- response에서만 사용되는 header 값들이 있음
	- cf) User-Agent -> Server 헤더

![](https://i.imgur.com/8rsG6Ju.png)
#### Body
- Response의 body와 일반적으로 동일
- Request와 마찬가지로 모든 response가 body가 있지는 않음
	- 전송할 필요가 없을경우 body가 비어있음

# **1. HTTP/1.0**

- 한 연결당 하나의 요청을 처리하도록 설계됨 -> RTT증가
	서버로부터 파일을 가져올 때 마다 [TCP의 3-웨이 핸드셰이크](https://yanacoding.tistory.com/entry/CS-TCPIP-4%EA%B3%84%EC%B8%B5-%EB%AA%A8%EB%8D%B8%EC%9D%B4%EB%9E%80%EA%B3%84%EC%B8%B5-%EA%B5%AC%EC%A1%B0-PDU)를 계속해서 열어야 하기 때문.
> - **RTT : Round Trip Time, 왕복 시간**
- 패킷이 목적지에 도달하고 나서 다시 출발지로 돌아오기까지 걸리는 시간

![https://blog.kakaocdn.net/dn/bT4vCL/btrNKU6DO6L/FRwgnUAW4shF5YQxqGCgH0/img.jpg](https://blog.kakaocdn.net/dn/bT4vCL/btrNKU6DO6L/FRwgnUAW4shF5YQxqGCgH0/img.jpg)

### **RTT의 증가를 해결하기 위한 방법**
- RTT가 증가 -> 서버에 부담이 많이 가고 사용자 응답 시간이 길어짐.
	이미지 스플리팅, 코드 압축, 이미지 Base64 인코딩 사용.

#### **이미지 스플리팅**
- 많은 이미지를 다운로드받게 되면 과부하 발생.
1. 많은 이미지가 합쳐 있는 하나의 이미지를 다운로드받고,
2. 이를 기반으로 background-image의 position을 이용하여 이미지를 표기.
```css
//하나의 이미지 background-image: url("icons.png");, background-position 등을 기반으로 이미지를 설정
#icons>li>a {
    background-image: url("icons.png");
    width: 25px;
    display: inline-block;
    height: 25px;
    repeat: no-repeat;
}
#icons>li:nth-child(1)>a {
    background-position: 2px -8px;
}
#icons>li:nth-child(2)>a {
    background-position: -29px -8px;
}
```

#### **코드 압축**
- 코드를 압축해서 개행 문자, 빈칸을 없애 코드의 크기를 최소화하는 방법.
```jsx
//코드 압축 전
const express = require('express')
const app = express()
const port = 3000
app.get('/', (req, res) => {
    res.send('Hello World!')
})

app.listen(port, () => {
    console.log(`Example app listening on port ${port}`)
})

//코드 압축 후
const express=require("express"),app=express(),port=3e3;app.get("/",(e,p)=>{p.send("Hello World!")}),app.listen(3e3,()=>{console.log("Example app listening on port 3000")});
```

#### **이미지 Base64 인코딩**
- 이미지 파일을 64진법으로 이루어진 문자열로 인코딩.
- 장점 : 서버와의 연결을 열고 이미지에 대해 서버에 HTTP 요청을 할 필요가 없음.
- 단점 : Base64 문자열로 변환할 경우 37% 정도 크기가 더 커질 수 있음.

# **2. HTTP/1.1**
- HTTP/1.0에서 발전한 프로토콜.
- 한 번 TCP 초기화를 한 이후에 keep-alive라는 옵션으로 여러 개의 파일을 송수신할 수 있음.
	cf) HTTP/1.0 처럼 매번 TCP 연결을 하는 것이 아님.
	HTTP/1.0에도 keep-alive존재. but 표준화가 되어 있지 않았었음.
	HTTP/1.1부터 표준화가 되어 기본 옵션으로 설정됨.
- 단점 : 문서 안에 포함된 다수의 리소스(이미지, css 파일, script 파일)를 처리하려면 요청할 리소스 개수에 비례하여 대기 시간이 길어짐

![https://blog.kakaocdn.net/dn/xzuvk/btrNKVqW7jG/d8EG6Gf3ZXmatOky0UE6lK/img.jpg](https://blog.kakaocdn.net/dn/xzuvk/btrNKVqW7jG/d8EG6Gf3ZXmatOky0UE6lK/img.jpg)

### **HOL Blocking(Head Of Line Blocking)**
- 네트워크에서 같은 큐에 있는 패킷이 그 첫 번째 패킷에 의해 지연될 때 발생하는 성능 저하 현상.

![https://blog.kakaocdn.net/dn/ccxrTy/btrNPzNereg/DOKEJyAs0XccIedj3aV6T0/img.jpg](https://blog.kakaocdn.net/dn/ccxrTy/btrNPzNereg/DOKEJyAs0XccIedj3aV6T0/img.jpg)

### **무거운 헤더 구조**
- HTTP/1.1의 단점 : 헤더에는 쿠키 등 많은 메타데이터가 들어 있고 압축이 되지 않아 무거움.
# **3. HTTP/2**
- SPDY 프로토콜에서 파생.
- SPDY 프로토콜 : 웹 콘텐츠를 전송할 목적으로 구글이 개발한 비표준 개방형 네트워크 프로토콜.
- HTTP/1.x보다 지연 시간을 줄이고 응답 시간을 더 빠르게 할 수 있음.
- 멀티플렉싱, 헤더 압축, 서버 푸시, 요청의 우선순위 처리를 지원.

#### **멀티플렉싱**
- 여러 개의 스트림을 사용하여 송수신 하는 것.
- 스트림 : 일반적으로 데이터, 패킷, 비트 등의 일련의 연속성을 갖는 흐름을 의미.
-  특정 스트림의 패킷이 손실되었다고 하더라도 해당 스트림에만 영향을 미치고 나머지 스트림은 영향받지 않음.

![https://blog.kakaocdn.net/dn/rPxem/btrNILoGYD6/CcOkxdfL0JTUBS8RQhoMpk/img.png](https://blog.kakaocdn.net/dn/rPxem/btrNILoGYD6/CcOkxdfL0JTUBS8RQhoMpk/img.png)

![https://blog.kakaocdn.net/dn/beCqEE/btrNM5s61TW/kEfhyyWpUptw2N8RKYGM00/img.jpg](https://blog.kakaocdn.net/dn/beCqEE/btrNM5s61TW/kEfhyyWpUptw2N8RKYGM00/img.jpg)

![https://blog.kakaocdn.net/dn/bOP5We/btrNNMs1GBs/yv42fg5UBn5ePM3w20DKRk/img.jpg](https://blog.kakaocdn.net/dn/bOP5We/btrNNMs1GBs/yv42fg5UBn5ePM3w20DKRk/img.jpg)

#### **헤더 압축**
- HTTP/1.x의 단점인 큰 헤더를 보완하기 위함.
- 허프만 코딩 압축 알고리즘을 사용하는 HPACK 압축 형식을 통해 헤더를 압축함.
##### **허프만 코딩(huffman coding)**
- 문자열을 문자 단위로 쪼개 빈도수를 세어 빈도가 높은 정보는 적은 비트 수를 사용하여 표현.
- 빈도가 낮은 정보는 비트 수를 많이 사용하여 표현해서 전체 데이터의 표현에 필요한 비트양을 줄임.

#### **서버 푸시**
- HTTP/1.1 : 클라이언트가 서버에 요청을 해야 파일을 다운로드 받을 수 있음.
- HTTP/2 :  클라이언트 요청 없이 서버가 바로 리소스를 푸시 가능.
	html을 읽으면서 그 안에 들어 있던 css 파일을 서버에서 푸시하여 클라이언트에 먼저 줌.

![https://blog.kakaocdn.net/dn/b2BjJk/btrNOd402De/vcf5ycIFasrnz0IuoWjAZK/img.jpg](https://blog.kakaocdn.net/dn/b2BjJk/btrNOd402De/vcf5ycIFasrnz0IuoWjAZK/img.jpg)

# **4. HTTPS**
- HTTP/2는 HTTPS 위에서 동작함.
- 통신 암호화 된 프로토콜, 즉 신뢰할 수 있는 HTTP 요청을 말함.
- 애플리케이션 계층과 전송 계층 사이에 신뢰 계층인 SSL/TLS 계층을 넣었기 때문.

### **SSL(Secure Socket Layer)/TLS(Transport Layer Security Protocol)**
- SSL 1.0-> SSL 2.0-> SSL 3.0-> TLS 1.0-> TLS 1.3.
- 버전이 올라가며 마지막으로 TLS로 명칭이 변경되었으나, 보통 이를 합쳐 SSL/TLS로 많이 부름.
- 전송 계층에서 보안을 제공하는 프로토콜.
	클라이언트와 서버가 통신할 때 SSL/TLS를 통해 제3자가 메시지를 도청하거나 변조하지 못하게 막음.
- 보안 세션을 기반으로 데이터를 암호화.
	보안 세션이 만들어질 때 인증 메커니즘, 키 교환 암호화 알고리즘, 해싱 알고리즘이 사용됨.

![https://blog.kakaocdn.net/dn/pv6d9/btrNPhTp9KB/inkO47MRHCMBFkxrQIOBUk/img.jpg](https://blog.kakaocdn.net/dn/pv6d9/btrNPhTp9KB/inkO47MRHCMBFkxrQIOBUk/img.jpg)

![https://blog.kakaocdn.net/dn/skXc8/btrNKghHBNN/CbGfrLNCKCTkYhS4B247rK/img.jpg](https://blog.kakaocdn.net/dn/skXc8/btrNKghHBNN/CbGfrLNCKCTkYhS4B247rK/img.jpg)

#### **보안 세션**
- 보안이 시작되고 끝나는 동안 유지되는 세션.
- **세션** : 운영체제가 어떠한 사용자로부터 자신의 자산 이용을 허락하는 일정한 기간.
    즉, 사용자는 일정 시간 동안 응용 프로그램, 자원 등을 사용할 수 있다.
- SSL/TLS는 핸드셰이크를 통해 보안 세션을 생성하고 이를 기반으로 상태 정보 등을 공유함.
- 클라이언트와 서버와 키를 공유, 이를 기반으로 인증, 인증 확인 등의 작업이 일어나는 단 한 번의 1-RTT가 생긴 후 데이터를 송수신.
- 클라이언트에서 사이퍼 슈트(cypher suites)를 서버에 전달
	CF)  0-RTT : TLS 1.3은 사용자가 이전에 방문한 사이트로 다시 방문한다면 SSL/TLS에서 보안 세션을 만들 때 걸리는 통신을 하지 않아도 되는것을 이름.
<br/><br/>
##### **사이퍼 슈트(cypher suites) : 암호화 스위트**
>  암호화 스위트의 구조![https://blog.kakaocdn.net/dn/WfJxK/btrNPikv0jL/3mdSHOm6uBD7tZXCfQEJ61/img.png](https://blog.kakaocdn.net/dn/WfJxK/btrNPikv0jL/3mdSHOm6uBD7tZXCfQEJ61/img.png)

-> 서버는 받은 사이퍼 슈트의 암호화 알고리즘 리스트를 제공할 수 있는지 확인
-> 제공할 수 있다면 서버에서 클라이언트로 인증서를 보내는 인증 메커니즘이 시작
-> 이후 해싱 알고리즘 등으로 암호화된 데이터의 송수신이 시작.

<br/><br/>
##### **AEAD(Authenticated Encryption with Associated Data) 사이퍼 모드**
-  AES_128_GCM 등 데이터 암호화 알고리즘.
<br/><br/>
##### **인증 메커니즘**
-  Comodo, GoDaddy, GlobalSign, 아마존등의 CA(Certificate Authorities)에서 발급한 인증서를 기반으로 이루어짐.
	인증서( 서비스 정보, 공개키, 지문, 디지털 서명 등으로 이루어짐)는 안전한 연결에  필요한 ‘공개키’를 클라이언트에 제공
	-> 사용자가 접속한 ‘서버가 신뢰’할 수 있는 서버임을 보장
<br/><br/>
##### **CA 발급 과정**
1) 자신의 사이트 정보와 공개키를 CA에 제출
2) 공개키를 해시한 값인 지문(finger print)을 사용하는 CA의 비밀키 등을 기반으로 CA 인증서를 발급
<br/><br/>
##### **암호화 알고리즘(키 교환 암호화 알고리즘)**
- 대수곡선 기반의 ECDHE(Elliptic Curve Diffie-Hellman Ephermeral) 또는 모듈식 기반의 DHE(Diffie-Hellman Ephermeral)를 사용.
	두 알고리즘 모두 디피-헬만(Diffie-Hellman) 방식을 근간으로 함.
	
<br/><br/>
##### **디피-헬만 키 교환 암호화 알고리즘(Diffie-Hellman key exchange) :**

![https://blog.kakaocdn.net/dn/Go4ED/btrNIKi2qPr/NfXR26sqjcy8TWON1i3zqK/img.png](https://blog.kakaocdn.net/dn/Go4ED/btrNIKi2qPr/NfXR26sqjcy8TWON1i3zqK/img.png)

![https://blog.kakaocdn.net/dn/oIfUp/btrNOTLYGtD/KEFlNZ77KTtZwSCHj8lnM1/img.png](https://blog.kakaocdn.net/dn/oIfUp/btrNOTLYGtD/KEFlNZ77KTtZwSCHj8lnM1/img.png)

<br/><br/>
##### **해싱 알고리즘**
- 데이터를 추정하기 힘든 더 작고, 섞여 있는 조각으로 만드는 알고리즘
- SSL/TLS는 해싱 알고리즘으로 SHA-256(가장 많이 사용) 알고리즘과 SHA-384 알고리즘을 사용.

<br/><br/>
##### **SHA-256 알고리즘**
- 해시 함수의 결괏값이 256비트인 알고리즘
- 비트 코인을 비롯한 많은 블록체인 시스템에서도 쓰임.
- 해싱을 해야 할 메시지에 1을 추가하는 등 전처리를 하고 전처리된 메시지를 기반으로 해시를 반환.

> - 해시 : 다양한 길이를 가진 데이터를 고정된 길이를 가진 데이터로 매핑(mapping)한 값

### **SEO(Search Engine Optimization)**
- **** HTTPS는 SEO에도 도움이 됨.(구글(Google)은 SSL 인증서를 강조해왔고 사이트 내 모든 요소가 동일하다면 HTTPS 서비스를 하는 사이트가 그렇지 않은 사이트보다 SEO 순위가 높을 것이라고 공식적으로 밝힘)
> SEO(Search Engine Optimization) : 검색엔진 최적화.
- SEO의 방법으론 캐노니컬 설정, 메타 설정, 페이지 속도 개선, 사이트맵 관리 등의 방법이 있음.
#### **캐노니컬 설정**
- 사이트 link에 캐노니컬을 설정

```jsx
<link rel="canonical" href="<https://example.com/page2.php>" />
```

#### **메타 설정**
- html 파일의 가장 윗부분인 메타를 잘 설정해야 함.
	해당 블로그도 구글 검색엔진에 등록하기 위해 메타를 별도로 설정해 두었다.

#### **페이지 속도 개선**
- [https://developers.google.com/speed/pagespeed/insights/](https://developers.google.com/speed/pagespeed/insights/) 등 페이지의 속도를 주기적으로 리포팅 받으며 관리해야 함.

#### **사이트맵 관리**
- 사이트맵은 다음과 같은 형식의 xml 파일을 말함.
	해당 블로드도 구글 검색엔진 노출을 높이기 위해 사이트맵을 등록해놓음.

```jsx
<?xml version="1.0" encoding="utf-8"?>
<urlset xmlns="<http://www.sitemaps.org/schemas/sitemap/0.9>">
<url>
<loc><http://kundol.co.kr/></loc>
<lastmod>수정날짜</lastmod>
<changefreq>daily</changefreq>
<priority>1.1</priority>
</url>
</urlset>
```

### **HTTPS 구축 방법**
1) CA에서 구매한 인증키를 기반으로 HTTPS 서비스를 구축.
2) 서버 앞단의 HTTPS를 제공하는 로드밸런서를 두어 구축.
3) 서버 앞단에 HTTPS를 제공하는 CDN을 두어 구축. 등

# **5. HTTP/3**
- HTTP/1.1 및 HTTP/2와 함께 World Wide Web에서 정보를 교환하는 데 사용되는 HTTP의 세 번째 버전.
- HTTP/3은 QUIC이라는 계층 위에서 돌아가며, TCP 기반이 아닌 UDP 기반으로 돌아감.
	CF)  HTTP/2 : TCP 위에서 돌아감.
- 장점 : HTTP/2에서 장점이었던 멀티플렉싱을 가지고 있으며, 초기 연결 설정 시 지연 시간 감소됨.

### QUIC : **초기 연결 설정 시 지연 시간 감소**
- QUIC은 TCP를 사용하지 않기 때문에 통신을 시작할 때 3-웨이 핸드셰이크 과정을 거치지 않아도 됨.
- QUIC은 순방향 오류 수정 메커니즘(FEC, Forword Error Correction)이 적용됨.
    따라서, 전송한 패킷이 손실되었다면 수신 측에서 에러를 검출하고 수정하는 방식이며 열악한 네트워크 환경에서도 낮은 패킷 손실률을 보임.
- 첫 연결 설정에 1-RTT만 소요됨.
	즉, 클라이언트가 서버에 어떤 신호를 한 번 주고, 서버도 거기에 응답하기만 하면 바로 본 통신을 시작.

![https://blog.kakaocdn.net/dn/Yt7N9/btrNNZsdRcJ/ohwFuVRupjr5W3lsNdGVN1/img.jpg](https://blog.kakaocdn.net/dn/Yt7N9/btrNNZsdRcJ/ohwFuVRupjr5W3lsNdGVN1/img.jpg)