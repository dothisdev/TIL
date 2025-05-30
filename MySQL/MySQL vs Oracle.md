# MySQL
## 특징
###### 라이센스
오픈소스로 무료로 제공
###### 고성능
인덱싱 및 최적화된 쿼리 실행을 지원 해 빠른 쿼리 처리를 제공
###### 확장성
대량의 데이터를 처리할 수 있고, sharding, replication을 통한 수평 확장을 지원
###### 데이터 보안
사용자 인증, 데이터 암호화, 접근 제어 기능을 제공
###### Replication
master-slave replication, clustering을 지원해 고가용성과 내결함성을 제공
# Oracle
## 특징
###### 고가용성
지속적인 가용성과 재해 복구를 보장하는 Real Application Clusters, Data Guard같은 고급 기능을 제공
###### 강력한 보안
암호화, 감사, 세분화된 접근 제어 등 다양한 보안 기능을 제공
###### 확장성 및 성능
파티셔닝, 인덱싱, 인메모리 처리를 통해 뛰어난 성능 제공
###### 멀티 모델 데이터베이스
관계형 데이터베이스뿐만 아니라 Document, Graph, XML 데이터베이스도도 지원
###### 엔터프라이즈 기능
고급 분석, 머신러닝, 자동화 도구를 제공하여 데이터 관리를 최적화함
###### 종합적인 도구 지원
개발, 관리, 비즈니스 인텔리전스에 대한 다양한 도구를 지원
## MySQL vs Oracle 비교

| **특징**     | **MySQL**                                                       | **Oracle**                                     |
| ---------- | --------------------------------------------------------------- | ---------------------------------------------- |
| **라이센스**   | 오픈 소스(엔터프라이즈 에디션은 추가 기능 제공)                                     | 상용 제품(엔터프라이즈 기능은 유료)                           |
| **비용**     | 커뮤니티 에디션은 무료, 엔터프라이즈 지원은 유료                                     | 라이선스 및 지원 비용이 높음                               |
| **성능**     | 읽기 중심 작업에 최적화, 인덱싱 및 쿼리 최적화 제공                                  | 복잡한 트랜잭션과 분석 작업에서 뛰어난 성능 제공                    |
| **확장성**    | 복제 및 샤딩을 통한 확장 지원                                               | RAC 및 Data Guard를 통한 강력한 확장성 제공                |
| **고가용성**   | 기본적인 복제 및 클러스터링 지원                                              | RAC 및 Data Guard 같은 고급 기능 제공                   |
| **보안**     | 기본적인 보안 기능(사용자 인증, 접근 제어) 제공                                    | 암호화, 감사, 세분화된 접근 제어 등 고급 보안 기능 제공              |
| **데이터 모델** | 주로 관계형 데이터베이스, 기본적인 JSON 처리 지원                                  | 관계형, 문서형, XML, 그래프 데이터 지원                      |
| **사용 편의성** | 단순하고 사용하기 쉬움                                                    | 광범위한 기능으로 인해 설정 및 관리가 복잡함                      |
| **지원**     | 커뮤니티 지원 제공, 엔터프라이즈 지원 가능                                        | 강력한 엔터프라이즈 지원 및 서비스 제공                         |
| **개발 언어**  | C, C++, Python, Ruby 등 다양한 언어 지원                                | 광범위한 프로그래밍 언어 및 개발 환경 지원                       |
| **데이터 유형** | 표준 SQL 데이터 유형 지원, 고급 데이터 유형은 제한적                                | XML 및 사용자 정의 데이터 유형을 포함한 다양한 데이터 유형 지원         |
| **복제 기능**  | **master-slave replication** 및 **master-master replication** 지원 | multi-master와 분산 데이터베이스를 포함해 고급 replication 제공 |
# Oracle vs MySQL
## Oracle
오라클은 대규모 엔터프라이즈 환경에 필요한 고가용성및 높은 확장성 지원을 포함한 고급 기능들, 높은 성능, 강력한 보안, 다양하고 강력한 지원을 제공하지만 높은 라이센스 비용과 높은 사양을 요구한다.
## MySQL
MySQL은 고급기능이 없지만 무료이며 가볍고 단순해 낮은 사양과 사용이 쉬우며 기본적인 기능을 제공하는 장점이 있다. 소규모 애플리케이션에 적합하다

###### 참고
https://www.geeksforgeeks.org/difference-between-oracle-and-mysql/
