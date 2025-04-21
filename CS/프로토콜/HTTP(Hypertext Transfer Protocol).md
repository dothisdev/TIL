---
tags:
  - http
---
# HTTP
![[Pasted image 20250416234835.png]]
HTTP는 웹에서 HTML 문서, JSON 파일, 스타일 시트, 비디오 파일, 이미지 파일등의 리소스를 가져올 수 있도록 하는 프로토콜이다
* 클라이언트-서버 프로토콜이라고 부른다
	* 클라이언트-서버 프로토콜은 수신자에 의해 요청이 초기화되는 프로토콜
* 통신의 기초는 클라이언트가 요청(request)하고 서버가 응답(response)한다
## HTTP 기반 시스템의 구성요소
##### 클라이언트: 사용자 에이전트
* 클라이언트는 대부분 브라우저
* 요청(request)을 보내는 존재
##### 웹 서버
* 클라이언트의 요청(request)을 응답(response)하는 존재
* 응답을 통해 리소스를 제공한다
#### 프록시
* 클라이언트의 HTTP 요청을 대신 처리하거나, 서버에 대신 전달하는 존재 
* 캐싱, 필터링, 로드 밸런싱, 인증, 로깅등을 수행함
* 클라이언트와 웹 서버는 프록시의 존재를 모름, 즉 투명하게 실행
## HTTP의 특징
##### 간단하다
사람이 읽을 수 있도록 간단하게 고안된 프로토콜
##### 확장 가능한 구조
HTTP 헤더를 통해 확장이 가능하다
##### 단방향 통신
클라이언트가 일반적으로 서버에게 통신 요청을한다
##### 비연결성
연결을 유지 않는다, 클라이이언트 서버가 통신하는 동안에만 연결을 유지하고 서버가 응답을 하고나서 연결을 끊는다
##### Stateless 구조 지만 세션은 구현할 수 있다
HTTP는 Stateless지만 HTTP 쿠키를 통해 세션을 구현할 수 있다
##### Connection에 관여
Connection은 전송 계층(4계층)에서 제어하기 때문에 HTTP(7계층)의 영역 밖이다 HTTP자체는 Connection을 제어하지 않고 에러가 적고 메시지 유실이 없는 안전한 Connection을 요구한다. 그래서 HTTP 프로토콜을 사용하면 TCP를 표준으로 사용하도록 한다. 왜냐하면 4계층 프로토콜로 TCP, UDP가 있는데 TCP가 연결 기반 프로토콜, UDP는 비연결 기반 프로토콜로 TCP가 신뢰성 있는 연결을 할 수 있기때문

> [!NOTE] HTTP프로토콜의 Connection에 대한 발전
> HTTP요청 전 여러번의 왕복이 필요한 TCP 연결을 설정하지만, 여러 요청을 보내는 경우 효율적이지 못함
> 그래서 HTTP/1.1은 파이프라이닝(구현 어려움) 개념, 지속적인 연결의 개념을 도입
> 그리고 HTTP/2는 단일 연결 에서 메시지 다중 전송을 도입
> 
> 그리고 현재 HTTP에 더 적합한 연결 기반 프로토콜를 연구중 그 예로 구글에서는 UDP기반 QUIC 프로토콜을 실험중
## HTTP의 단점
* 중간에서 패킷을 가로채어 내용을 엿보거나 변조할 수 있다 즉 보안에 취약
	* 이를 극복하기 위해 HTTPS가 개발되엇다 SSL/TLS 프로토콜을 통해 세션 데이터가 암호화한 상태 전송
## HTTP 메소드
![[Pasted image 20250417014710.png]]
* 안전 : 호출해도 리소스가 변경되지 않는것
* 멱등 : 여러번 호출해도 1번 호출한것과 같은 효과를 지닌것
* 캐시 : 응답 결과를 서버에서 캐시 하여 사용개도 되는 메소드
	* POST, PATCH는 실무에서 구현이 어려워 일반적으로 GET, HEAD만 사용
## HTTP 상태 코드
![[Pasted image 20250417015018.png]]
https://developer.mozilla.org/ko/docs/Web/HTTP/Reference/Status
## HTTP가 제어가능한것
* 캐시
	* HTML 문서, 이미지 파일과 같은 리소스에 대한 캐시 제어 가능
* origin 완화
	* 기본적으로 동일한 origin만 전체 정보를 접근할 수 있지만 완하 할 수 있다
* 인증
	* 인증 설정을해 특정 사용자만 리소스에 접근하도록 할 수 있다
* 프록시
* 세션
	* 쿠키 설정을 통해 세션 유지 가능
## HTTP 흐름
클라이언트 서버가 통신할때 다음과 같은 흐름을 가진다, 서버가 프록시든 웹 서버든 상관없이 다음 흐름을 가진다
1. TCP 연결을 연다, TCP 연결을 통해 요청을 보내거나 응답을 받을 수 있다 클라이언트는 새 연결을 열거 나 기존 연결을 재사용하거나, 여러 TCP연결을 열 수 있다
2. HTTP 메시지를 전송(request)
```http
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```
3. HTTP 응답 메시지를 읽음(response)
```http
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html

<!DOCTYPE html... (here comes the 29769 bytes of the requested web page)
```
4. TCP 연결을 닫거나, 다른 요청을 위해 재사용

> [!NOTE] HTTP 다중 요청
> HTTP 파이프라이닝을 통해 동시에 여러 요청을 보낼 수 있지만 구현이 어려운 단점이 있어 프레임안에서 보다 활발히 다중 요청을 보내는 HTTP/2로 교체되어진 상태

## HTTP 메시지
#### 변천사
HTTP/1.1와 이전에는 메시지를 사람이 읽을 수 있다
HTTP/2 이후 메시지를 이진 프레임구조로 캡슐화하여, 헤더 압축 다중화등의 최적화를 실행함, 그렇지만 클라이언트는 해당 메시지를 복호화 하기 때문에 결과적으로 메시지를 여전히 사람이 이해할 수 있음
#### request 메시지
![[http-request.svg]]
* HTTP 메소드
* 요청 리소스 경로
* 프로토콜 버전
* 헤더
* body
#### response 메시지
![[http-response.svg]]
* 프로토콜 버전
* 상태 코드
* 상태 메시지
* 헤더
* body

##### 참고
https://developer.mozilla.org/ko/docs/Web/HTTP/Guides/Overview
https://bruders.tistory.com/143
https://girawhale.tistory.com/66