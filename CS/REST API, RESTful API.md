![[Pasted image 20250416015153.png]]
# REST API
### REST API(Representational State Transfer)란
* 월드 와이드 웹(WWW)과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 개발 아키텍처의 형식
* 웹의 기존 기술, HTTP 프로토콜을 그대로 활용하여 웹의 장점을 최대한 활용가능한 웹 아키텍처 스타일
* REST를 따르는 아키텍처는 ROA(Resource Oriented Architecture) 다
	* HTTP Method를 통해 Resource를 처리하는 구조
* REST를 따르면 **플랫폼에 독립적인 서버를 설계**할 수 있다
	* REST이전에는 플랫폼이 적어 표준 규약 없이 특정 플랫폼에 특화된 서버를 설계하지만 현재 플랫폼이 많아지면서 많은 서버를 관리해야해 플랫폼에 독립적인 표준 아키텍처 스타일인 REST가 등장함
## REST 구성
* 자원 - URL
	* URL를 통해 자원을 접근할 수 있다
	* 자원은 고유한 ID가 존재하며, 서버에 보관되어있다.
	* 자원을 구별하는 ID는 /products/product_id/1와 같은 HTTP URI
* 행위 - Method
	* HTTP 프로토콜의 Method를 의미
* 표현 - Representaion of Resource
	* 자원의 행위에 대한 응답이다
	* JSON, XML, TEXT, RSS등의 형태로 서버는 응답(Representation)한다
	* 현재 REST는 JSON로 주로 응답
## REST 특징
#### 클라이언트 / 서버 구조
* 클라이언트는 사용자와 관련된 처리, 서버는 REST API를 제공하게 하여 각각의 역할을 구분짓고 일관적 인터페이스로 분리되어 동작시킨다
* REST Server: REST API를 제공하고 비즈니스 로직 처리 및 저장을 책임진다.
* Client: 사용자 인증 정보, 사용자 상태 context(세션, 토큰, 로그인 정보) 등을 직접 관리하고 책임진다.
* 클라이언트와 서버 사이의 의존성이 줄어든다
#### 무상태성 (Stateless)
* REST가 활용하는 HTTP의 특징인 무상태성을 그대로 가진다
* 무상태성을 통해 상태정보 처리를 책임지지 않아도 되서 구현이 쉬워지고, 서버 증설도 쉬워진다
#### 캐시 처리 기능 (Cashable)
* REST가 활용하는 HTTP의 특징인 캐시 처리 기능을 그대로 가진다
* 캐시를 활용하면 REST Server의 트랜잭션이 발생되지 않기때문에 빠른 응답, 성능 향상, 효율적인 자원 사용가능
#### 자체 표현 구조 (Self - descriptiveness)
* JSON등의 응답 메시지 포맷을 활용하여 직관적인 이해와, REST API 메시지로 요청이 어떤 행위인지 파악 가능
#### 계층화 (Layered System)
* REST로 클라이언트와 서버가 계층으로 분리되어 중간에 프록시 서버, 암호화 계층 등의 사용이 가능
#### 유니폼 인터페이스 (Uniform)
* 플랫폼에 독립적인 표준 인터페이스를 통해 플랫폼에 자유롭게 통신이 가능
## REST 특징
#### 코어 규칙
* URI는 정보의 자원을 표현
* 자원에 대한 행위는 HTTP Method로 표현
#### 세부 규칙
* 슬래시 구분자 (/)는 계층 관계를 나타내는데 사용
* URI 마지막 문자에는 슬래시(/)를 포함시키지 않는다
* 하이픈( - )은 URI 가독성을 높이는데 사용
* 밑줄( _ )은 URI에 사용하지 않는다
* URI 경로는 소문자가 적합
* 파일확장자는 URI에 포함시키지 않는다
* 리소스 간에 연관관계가 있는경우 (/리소스명/리소스ID/관계가 있는 다른 리소스명) 으로 URI를 표현한다
## REST API 설계 목표
* 상호연동성 확보
	* 상호연동성이란 서로 다른 컴포넌트끼리 유연하게 연결하는 성질을 말한다
	* REST는 HTTP와 URI기반으로 HTTP, URI는 표준 제약에 따라 직관적으로 사용이 가능하고 어디서든 동일한 인터페이스를 제공한다.
* 범용 인터페이스
	* REST API는 HTTP와 URI기반으로 어느 플랫폼에서든 사용가능한 표준 인터페이스를 제공한다
* 각 컴포넌트들의 독립적인 배포
	* REST API를 통해 클라이언트/서버가 분리되어 컴포넌트들이 독립적으로 개발되고 배포될 수 있게한다
	* 컴포넌트 형태로 다른 컴포넌트의 추가가 쉽다
* 컴포넌트를 중계하는 역할
	* REST 서버는 클라이언트와 엔드서버의 중계서버를 담당
	* 중계 서버는 로드 밸런싱, 공유 메모리로 등을 이용해 확장성/ 성능 향상이 가능, 보안 정책 적용도 가능
![[Pasted image 20250416030908.png]]
# RESTful API
## RESTful 이란
* REST아키텍처를 따르는 API
* RESTful이란 의미는 완벽히 REST를 따르는 API를 의미하기도 한다
## RESTful API 설계 원칙
#### 자원을 식별할 수 있어야한다
* URL(Uniform Resource Locator)를 통해 어떤 자원을 제어하려는지 알 수 있어야한다.
* Server는 정보를 HTTP Body에 JSON, XML 포맷에 맞춘 정보를 포함하여 전송한다
#### 행위는 명시적이어야 한다
* HTTP Method에 맞춰 API는 RESOURCE를 처리해야한다
* 이를 지키지 않으면 RESTful API라고 볼 수 없다.
	* e.g) get api에서 post행위가 발생
#### 자기 서술적이어야 한다
* 데이터에 대한 메타 데이터를 통해 어떤 종류의 데이터인지, 데이터를 위해 어느 애플리케이션을 실행해야 하는지 알 수 있어야 함
* 데이터 처리를 위한 정보를 얻기 위해, 메타 데이터가 아닌 데이터 원본을 읽는다면 자기 서술적이지 못함
```json
{
  "filename": "report.pdf",
  "type": "application/pdf",
  "url": "https://example.com/files/123"
}
```
다음 메타 데이터를 통해 1. 어떤 종류의 데이터(pdf)인지 2. 데이터(pdf)를 위해 어느 애플리케이션(pdf viewer)을 실행해야 하는지를 알 수 있음
#### HATEOS(Hypermedia as the Engine of Application State)여야 한다
* 클라이언트의 요청에 응답할때 자원에 추가적으로 연결되는 링크를 포함시켜야 한다
* API에 링크가 제공되어 문서 없이 연결되는 링크를 알 수 있다
* HATEOS를 통해 동적으로 링크에 접근해 서버와 클라이언트가 더 독립적으로 동작한다.
## REST의 단점
* REST는 point-to-point 통신모델을 베이스로 하기때문에 서버 클라이언트가 서로 연결되어 상호작용하는 애플리케이션 개발에는 적절하지 않음
* REST는 URI, HTTP를 이용한 아키텍처 설계론이기 때문에 보안과 통신규약 정책은 다루지 않는다
* HTTP에 의존적이라 REST설계 원칙을 통해 다른 프로토콜 구현이 힘든편
* CRUD 4가지 메소드만 제공

### 참고
https://velog.io/@somday/RESTful-API-%EC%9D%B4%EB%9E%80#rest-api