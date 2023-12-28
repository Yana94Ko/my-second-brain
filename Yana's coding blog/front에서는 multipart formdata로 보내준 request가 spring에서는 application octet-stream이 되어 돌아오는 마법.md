---
tistoryBlogName: yanacoding
tistoryTitle: front에서는 multipart formdata로 보내준 request가 spring에서는 application octet-stream이 되어 돌아오는 마법
tistoryVisibility: "3"
tistoryCategory: "1049239"
tistorySkipModal: false
tistoryPostId: "232"
tistoryPostUrl: https://yanacoding.tistory.com/232
---
# obsidian에서 작성중

MultipartResolver를 bean으로 설정해주어야 하는가? No
spring 어플리케이션의 경우 web.xml에서 MultipartResolver를 bean으로 직접 등록해주어야 하지만, spring boot 어플리케이션은 default로 제공한다.