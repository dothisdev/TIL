# NoSQL
NoSQL(Not Only SQL)은 기존 관계형 데이터베이스와 다르게 구조화 데이터뿐만 아니라 반구조화, 비구조화 데이터를 저장할 수 있다.

주로 빅데이터, 실시간 분석, 분산 환경에 사용된다.
## 특징
### 확장성
하나의 서버를 업그레이드 하는 대신 여러 서버를 추가해 수평확장이 가능하다.
### 유연성
유연한 스키마로 반구조화, 비구조화 데이터를 저장할 수 있다.
### 고성능
대용량 데이터의 읽기/쓰기 작업에 최적화 되어 있다
### 분산 아키텍처
분산 시스템에서 높은 가용성과 파티션 내성을 제공하도록 설계되었다
## 장점
* 반구조적, 비구조적 데이터 저장이 가능하다
* 쉬운 수평 확장을 지원한다
* 대량의 데이터를 빠르게 읽고 쓸 수 있다
* 복잡성이 낮고, 저비용으로 동작
* 애자일 개발에 유용
## 단점
* 대부분 NoSQL은 ACID를 보장하지 않아 데이터 일관성이 부족
* 트랜잭션 관리 기능 부족
## 유형
### Document Database
JSON 형식으로 데이터를 저장
e.g) MongoDB, CouchDB
**적합한 사용 사례:** 콘텐츠 관리 시스템(CMS), 사용자 프로필, 카탈로그
### Key-Value Database
Key-Value 쌍으로 데이터를 저장
주로 캐싱 및 세션 저장 용도로 최적화
e.g) Redis, Memcached, Amazon DynamoDB
**적합한 사용 사례:** 세션 관리, 실시간 데이터 캐싱, 리더보드 시스템
### Wide-Column Database
데이터를 테이블에서 행마다 서로 다른 열로 저장
고속 분석과 분산 컴퓨팅에 적합함.
대량의 데이터 처리 및 높은 읽기/쓰기 성능을 요구하는 환경에 최적화됨.
e.g) Apache Cassandra, HBase, Google Bigtable
**적합한 사용 사례:** 시계열 데이터, IoT 애플리케이션, 빅데이터 분석
### Graph Database
데이터를 노드와 엣지 형태로 저장
노드는 주로 사람, 장소, 사물과 같은 객체에 대한 정보를 엣지는 노드 간의 관계에 대한 정보를 저장

관계나 패턴이 명확하지 않을 수 있는 고도로 연결된 데이터에 적합
e.g) Neo4j, Amazon Neptune, ArangoDB
**적합한 사용 사례:** 관계 기반 쿼리가 필요한 애플리케이션(예: 사기 탐지, 소셜 네트워크 분석)
##### 참고
https://www.mongodb.com/ko-kr/resources/basics/databases/nosql-explained
https://www.geeksforgeeks.org/introduction-to-nosql/