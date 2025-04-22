![[Pasted image 20250422220649.png]]
# WebSocket
* 프로토콜은 ws:// or wss://
* 양방향 통신 프로토콜
* 연결을 유지
* stateful
* TCP기반
* HTTP와 같은 7계층 프로토콜
게임, 채팅, 알림, 주식 차트같은 실시간 앱에 사용

## WebScoket 연결과정
1. 클라이언트가 WebSocket요청을 하기전 TCP 3-Way Handshake를 통해 TCP연결이 설정
2. 클라이언트가 Upgrade: websocket를 헤더에 담아 HTTP 요청을한다.
3. 서버는 101 Switching Protocols 응답과 함께 HTTP 프로토콜을 WebSocket 프로토콜로 전환한다
4. 클라이언트는 101 Switching Protocols 응답을 받고 HTTP 프로토콜을 WebSocket 프로토콜로 전환
###### 참고
https://www.geeksforgeeks.org/what-is-web-socket-and-how-it-is-different-from-the-http/