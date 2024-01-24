---
tistoryBlogName: yanacoding
tistoryTitle: "[AWS] 아마존 벽돌 그만 사주기 프로젝트, Resource Consolidation(월 15만원 - >2만원)"
tistoryVisibility: "0"
tistoryCategory: "1052524"
tistorySkipModal: true
tistoryPostId: "269"
tistoryPostUrl: https://yanacoding.tistory.com/269
---
# <obsidian에서 작성중>
# AWS.. 월 청구 비용 25만원. 이게 정말 맞나요?(클라우드에 대한 이해 없이 진행한 배포의 비싼 수업료)
![](https://i.imgur.com/LenCCtt.png)

![](https://i.imgur.com/CB7qMLT.png)

&nbsp;&nbsp;EC2 인스턴스 2개에서 spring - jsp 프로젝트와 node-react 프로젝트를 돌리던 어느날, 어마무시한 청구서가 날아왔다. 팀프로젝트를 진행하며 동일한 DB를 사용하기위해 공유했던 각 프로젝트들의 RDS 인스턴스와 더불어서, node-react에 대한 이해 없이 백엔드와 프론트엔드 각각의 js 런타임을 서버에서 돌리기 위해 규모가 큰 EC2인스턴스를 사용한 결과였다. AWS 클라우드와, Node 그리고 JS의 런타임에 대한 이해의 부족이 만들어낸 눈덩이같은 결과였다.

&nbsp;&nbsp;이에, 우선 사용중인 AWS 서비스들이 정말 필요한지 판단을 하기 시작했는ㄷ, 포트폴리오를 위한 서비스들이었고, 유저가 없던 상황이기에 각각의 서비스별로 트래픽이 많지 않아 콜리다운을 하더라도 문제가 발생할 확률이 적어보였다. 따라서 굳이 분산되지 않아도 되었을 RDS부터 시작해서 각각 인스턴스에 흩어져있는 서비스들을 콜리다운하기로 결정했다. 




# RDS Consolidation 과정
&nbsp;&nbsp;RDS의 경우 우선 네트워크 비용을 줄이기 위해 각각의 리전에 흩어져있던 RDS 인스턴스를 한국 리전으로 옮겨오는 작업부터 진행했다가, mysql dump를 이용해 하나의 인스턴스로 합치는 작업을 진행했다.
- [[mysqlDump] DB 합치기.. 그거 어떻게 하는건데.....? (feat.. mysqldump)](https://yanacoding.tistory.com/entry/mysqlDump-DB-%ED%95%A9%EC%B9%98%EA%B8%B0-%EA%B7%B8%EA%B1%B0-%EC%96%B4%EB%96%BB%EA%B2%8C-%ED%95%98%EB%8A%94%EA%B1%B4%EB%8D%B0-feat-mysqldump)
+ RDS 리전 변경(Feat 스냅숏)
# EC2 Consolidation 과정


&nbsp;&nbsp;EC2인스턴스의 경우엔 JS중 frontend를 정적으로 build하여 배포함과 동시에, 하나의 인스턴스에 여러 프로젝트를 올려놓고 리버스 프록싱을 해주기로 결정했다. 관련해서 배포를 편하게 진행하기 위해 Docker와 Docker Compose를 이용하기러 했고, CD를 구성해 자동으로 배포가 진행될수 있도록 설정하는 과정까지 거쳤다.
- [[Docker] 도커... 그래서 그게 뭔데...?](https://yanacoding.tistory.com/entry/Docker-%EB%8F%84%EC%BB%A4-%EA%B7%B8%EB%9E%98%EC%84%9C-%EA%B7%B8%EA%B2%8C-%EB%AD%94%EB%8D%B0)
- [[Docker Cross-Platform Build 방법과 원리(feat m1 mac에서 빌드한 image, 왜 ubuntu서버에서 돌아가지 않는다?!)]]
- [[Docker compose, Docker hub, webhook, node.js를 활용한 야매 CD 개발기]]

# 결과
## 안녕하세요, AWS에 벽돌 '덜'사주기 시작한 Yana입니다.
![](https://i.imgur.com/3eGLtV8.png)

# 추후 학습 방향
- 너무 작은 인스턴스에 Server Consolidation를 진행한 결과 Java-spring 어플리케이션이 메모리 부족으로 특정 주기마다 죽는 이슈가 발생했다.
- 이를 해결하기 위해 시도해볼수있는 방법이 아래와 같이 있는데, 각각의 빙밥은 시간이 나는대로 시도해보고 과정을 기록하고자 한다.
	- 서버를 스케일 업한다
	- java 어플리케이션이 돌아가고있는 각각 Docker 의 container가 사용할수있는 메모리를 제한하도록 설정
	- 각 어플리케이션 JVM의 메모리 제한
	- DB의 connection관련 이슈로 hikariCP를 공부해 커넥션을 관리
	- 클라우드가 아닌 local에서 포트를 열어 서비스 배포
