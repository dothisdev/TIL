---
tags: http
---
![[Pasted image 20250418002706.png]]
# HTTPS
HTTPS는 HTTP의 암호화된 버전이다
HTTPS는 SSL/TLS 프로토콜을 사용해
데이터 전송을 암호화해 도청, 변조등의 보안 위협을 방지한다.

> [!NOTE] SSL과 TSL의 관계
> SLL은 구버전 보안 프로토콜로 현재는 TLS로 대체 되었다
> 최신 웹 에서는 TLS가 사용되고 잇으며, 아직도 SSL이라는 용어가 많이 사용되어 혼동의 여지가 존재
## 장점
1. 데이터를 암호화해 탈취나 변조를 막는다
2. 구글같은 검색엔진은 HTTPS 웹사이트를 더 상위로 노출해준다 -> SEO 향상
## TLS 암호화 방식
TLS는 인증서, 공개키, 개인키, 세션키를 사용하여 데이터를 암호화, 서버 인증, 데이터 무결성 유지가 가능하다

TLS 프로토콜을 방식은 TLS Handshake과정을 거쳐 이러한 것들을 얻을 수 있다
![[Pasted image 20250418002856.png]]
### TLS Handshake
TLS Handshake는 서버와 클라이언트가 안전한 데이터 교환을 위한 과정이라고 생각하면 된다.
TLS Hansshake과정을 통해 서버와 클라이언트가 서로 사용할 알고리즘을 의논하고, 인증서를 통해 서버가 안전한 서버인지 인증하고, 클라이언트는 세션키를 공개키로 암호화해 전달하고 서버는 세션키를 개인키로 복호화해 서로 대칭키가 준비되면 안전한 통신이 가능한 상태가된다.
#### 과정
###### 1. ClientHello
Client는 자신이 사용가능한 암호화 알고리즘, SSL 프로토콜 버전, 클라이언트 랜덤이라 불리는 랜덤 바이트 문자열을 서버에게 전송한다
###### 2. ServerHello
서버는 SSL 인증서, 서버가 선택한 암호화 알고리즘, 서버 랜덤이라 불리는 랜덤 바이트 문자열을 클라이언트에게 전송
###### 3. Authentication 
클라이언트는 인증서를 발급한 인증기관을 통해 서버가 안전한지 검증
###### 4. The premaster secret
클라이언트는 premaster secret이라 불리는 랜덤 바이트 문자열을 공개키로 암호화(서버의 개인키로 복호화 할 수 있다)해 서버에게 전달
###### 5. Private key used
서버는 premaster secret을 개인키를 통해 복호화한다
###### 6. Session keys created
클라이언트와 서버는 서버 랜덤, 클라이언트 랜덤, premaster secret을 통해 세션 키를 생성한다
###### 7. Client is ready
클라이언트는 "완료" 메시지를 세션키로 암호화해 전송
###### 8. Server is ready
서버도 "완료" 메시지를 세션키로 암호화해 전송 
###### 9. Secure symmetric encryption achieved
클라이언트와 서버는 서로 대칭키를 갖게 되었고 세션이 유지되는동안 안전한 통신이 가능해진다
##### 참고
https://www.cloudflare.com/ko-kr/learning/ssl/what-is-https/
https://www.cloudflare.com/ko-kr/learning/ssl/what-happens-in-a-tls-handshake/
https://aws-hyoh.tistory.com/39

