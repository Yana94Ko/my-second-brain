---
tistoryBlogName: yanacoding
tistoryTitle: "[Ncloud, AWS] aws밖에 모르던 클라우드린이의 Ncloud 적응기(Feat.. 클라우드에 대한 이해)"
tistoryTags: AWS,Ncloud,네이버클라우드,ec2,rds,route53,s3,server,cloud db for mysql, cloudmonitoring,global dns
tistoryVisibility: "3"
tistoryCategory: "1052524"
tistorySkipModal: true
tistoryPostId: "268"
tistoryPostUrl: https://yanacoding.tistory.com/268
---
# <Obsidian 에서 작성중>

## 기존에 사용하던 AWS 클라우드 기능
- EC2
- RDS
- Route 53
- S3

## 외주 프로젝트에서 사용하게된 Ncloud
- Server
- Cloud DB for MySQL
- Global DNS
- Object Storage
- Cloud Insight

## 각각 대응하는 서비스
 - EC2 -> Server
- RDS -> Cloud DB for MySQL
- Route 53 -> Global DNS
- S3 -> Object Storage
## Ncloud 아쉬운점과 왜 AWS와는 다른 방식을 사용하는지에 대한 고민
### SERVER : 인스턴스 ssh 접속과 포트포워딩
- ssh에서 ssh키를 통한 접근이 막혀있는 이유
	- ssh를 통해 온라인 console에 로그인 한 뒤 비밀번호를 확인하고, 해당 비밀번호를 통한 ssh접속만 지원함
- 서버 접속용 공인 IP가 필요한 이유
	- zone에 대해 알아보고 클라우드 컴퓨팅의 구성 이해하기
	- 설정하도록 되어있는 포트포워딩을 기반으로 흐름도 그려보기
### Cloud DB for MySQL(RDB) : 불편함을 감내하는 안정성?
- 콘솔 접속을 통한 DB Config와, 인스턴스 내 DB 생성, User 설정이 막혀있는 이유 고민해보기
## Ncloud에서의 AWS(Feat..AWS S3 SDK 지원)
- Ncloud에서 Object Storage를 사용할 때 AWS의 SDK와 AWS관련 Spring 기능들을 사용하는 이유
	- 초기 : 아직 독립적인 SDK를 구성하지 못한건 아닐까?
	- 현재 : 기존 AWS사용자의 Ncloud 도입을 보다 쉽게 하기 위해서일 수 있겠다.
## 추후 학습 방향
- 클라우드 컴퓨팅의 구성 이해하기
- RDB인스턴스의 특성과, 안정성에 대해서 이해하기
	- docker를 통해 DB를 띄우는걸 지양했던 이유
- 클라우드 모니터링 관련해서 공부해보기
	- 모니터링을 설정하기 쉽지 않았던 이유 : 언제 어떠한 경보를 받아야하는지 결정하기 쉽지 않았음. 클라우드와 서버에 대한 이해가 부족했기 때문이라고 판단.