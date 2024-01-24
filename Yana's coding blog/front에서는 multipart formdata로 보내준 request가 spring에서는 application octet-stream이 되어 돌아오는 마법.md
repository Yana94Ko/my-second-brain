---
tistoryBlogName: yanacoding
tistoryTitle: front에서는 multipart formdata로 보내준 request가 spring에서는 application octet-stream이 되어 돌아오는 마법(HTTP 표준과 content type, multipart formdata)
tistoryVisibility: "3"
tistoryCategory: "1052524"
tistoryPostId: "232"
tistoryPostUrl: https://yanacoding.tistory.com/232
---
# obsidian에서 작성중

MultipartResolver를 bean으로 설정해주어야 하는가? No
spring 어플리케이션의 경우 web.xml에서 MultipartResolver를 bean으로 직접 등록해주어야 하지만, spring boot 어플리케이션은 default로 제공한다.

## HTTP 표준과 content type
HTTP 표준은 1개의 요청에는 하나의 content type만 전송하는것을 약속함.
(여러개의 content 타입을 전송하는것이 불가능한것은 아님.)

## multipart formdata가 여러 content-type를 보낼수 있도록 만들어진 것 아닌가?
### multipart formdata란?

### 디버깅으로 밝혀진 @ReuestParam의 반란

## 이미지 등의 file 업로드를 별도의 api로 분리하는 이유
### HTTP 표준을 지키자?
### 비동기 통신과 재시도의 관점에서 바라보기
# 추후 학습 방향
- 다양한 비동기 통신 방법에 대해 알아보기
- 표준을 잘 지키는 개발을 하기 위해서는 어떤 부분을 신경써야 할 까?