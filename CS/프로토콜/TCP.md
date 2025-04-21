# TCP
TCP는 Transport Layer(4 Layer)에 있는 프로토콜이다.
* 신뢰성 있는 전송을 보장한다.
* 연결 지향성
* 손상된 패킷 감지, 패킷 재전송
* 흐름 제어
	* 패킷의 사이즈, 순서등을 파악해 TCP끼리 안정적인 흐름으로 패킷 전달
* 혼잡 제어
	* 네트워크의 혼잡함에 따라 적절한 패킷을 전달
* 순서 보장
![[Pasted image 20250422020333.png]]
## TCP 3-Way Handshake
TCP 3-Way Handshake는 신뢰성 있는 TCP연결을 하는 과정이다.
3번의 철저한 확인을 통해 안정적인 연결을 보장할 수 있다.
* 양쪽 모두 연결을 확인한다
* 양쪽 모두 상대편의 초기 sequence number를 획득한다
###### 1. SYN - CLIENT
클라이언트는 서버에게 접속을 요청하는 SYN 패킷을 보낸다. 그리고 클라이언트는 SYN/ACK응답을 기다리는 SYN_SENT 상태가 된다
###### 2. SYN+ACK - SERVER
서버는 SYN 패킷을 받고 접속을 수락하는 ACK와 SYN FLAG가 설정된 패킷을 클라이언트에게 발송한다, 이후 서버는 클라이언트의 ACK를 기다리는 SYN_RECEIVED 상태가 된다
###### 3. ACK - CLIENT
클라이언트는 서버에게 ACK를 보내고 서버는 정상적으로 받게되면 TCP 연결이 성공적으로 이루어지고 신뢰성 있는 데이터 전송이 가능하다. 이때 서버와 클라이언트 모두 ESTABLISHED 상태가 된다.
![[Pasted image 20250422045449.png]]
## TCP 4-Way Handshake
TCP 4-Way Handshake는 TCP연결을 안전하게 해제하는 과정이다.
###### 1. FIN - CLIENT
클라이언트가 연결을 종료하는 FIN 패킷을 보낸다
###### 2. ACK - SERVER
서버는 ACK 패킷을 클라이언트에게 보낸다. 그리고 연결을 종료할 준비를 한다
###### 3. FIN - SERVER
서버가 연결을 해제할 준비가 완료되었다면 FIN패킷을 클라이언트에게 보낸다
###### 4. ACK - CLIENT
클라이언트는 ACK 패킷을 서버에게 보내면서 연결이 종료된다.

Server에서 FIN 패킷 전송전에 보낸 패킷이 손실로 인한 재전송으로 인해 FIN 패킷보다 늦게 도착할 수 있다. 하지만 이러한 상황에 Client에서 서버에서 FIN을 수신하더라도 일정시간동안 세션을 유지해 이러한 늦게 오는 패킷을 기다려 대비할 수 있고 이러한 상태를 TIME_WAIT라고 부른다

###### 참고
https://mindnet.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-22%ED%8E%B8-TCP-3-WayHandshake-4-WayHandshake