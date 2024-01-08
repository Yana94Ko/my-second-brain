---
tistoryBlogName: yanacoding
tistoryTitle: "[작성중]GraphQL - 프론트엔드에서 쿼리를 마음껏 날릴 수 있다고? (보안과 권한은 어디로 가는가.. Injection은? REST와의 차이점은 뭘까?)"
tistoryTags: DB,GraphQL,협업,백엔드,프론트엔드,Injection,SEARCH
tistoryVisibility: "3"
tistoryCategory: "1154897"
tistorySkipModal: true
tistoryPostId: "244"
tistoryPostUrl: https://yanacoding.tistory.com/244
---
# <Obsidian 에서 작성중>

프론트엔드와 백엔드 개발자의 협업에 대해 이야기 나누던 도중, 기능 개발 분업 관련 이슈에 대한 대응방법중 하나로 GraphQL에 대한 이야기가 나왔다. 

사실 GraphQL이라는 키워드는 몇번 들어 본 적이 있는데 graphQL이라는 이름만 듣고 'SQL과 같은 RDBMS를 다루는 일종인가?'라는 추측만 해왔던지라, 어떻게 graphQL이 프론트엔드와의 협업에서 하나의 방인이 될 수 있는지 궁금해져 찾아보게 되었다.

# [GraphQL](https://graphql.org/)
- 페이스북(Meta)에서 만든 쿼리 언어 : 또 페이스북인가..!
- Graph QL(이하 gql)은 Structed Query Language(이하 sql)와 마찬가지로 쿼리 언어

### SQL과 GraphQL 차이
- 목적
	- SQL :  **데이터베이스 시스템**에 저장된 데이터를 효율적으로 가져오는 것
	- GQL : **웹 클라이언트**가 데이터를 서버로 부터 효율적으로 가져오는 것
- 작성과 호출의 주체
	- SQL : 주로 백앤드 시스템에서 작성하고 호출
	- GQL : 주로 클라이언트 시스템에서 작성하고 호출
- 쿼리 예시
```sql
# SQL
SELECT plot_id, species_id, sex, weight, ROUND(weight / 1000.0, 2) FROM surveys;
```
```graphql
# GraphQL
{
  hero {
    name
    friends {
      name
    }
  }
}
```

# REST API와의 차이점

# GraphQL 구조와 동작방식

# DB를 다루는건데.. 보안은..? 권한은..? 어떻게 관리되지?
## 쿼리문이 클라이언트로부터 날아온다.. Injection은?

# GraphQL과 같은 양식을 위해 검토된다던 HTTP 메서드 SEARCH의 근황?
