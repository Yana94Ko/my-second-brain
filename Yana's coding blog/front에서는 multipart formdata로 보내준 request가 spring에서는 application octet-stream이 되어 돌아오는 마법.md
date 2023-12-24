MultipartResolver를 bean으로 설정해주어야 하는가? No
spring 어플리케이션의 경우 web.xml에서 MultipartResolver를 bean으로 직접 등록해주어야 하지만, spring boot 어플리케이션은 default로 제공한다.