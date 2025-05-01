###### 1. 웹 브라우저에서 URL를 입력
###### 2. 웹 브라우저에 도메인명의 IP 주소 조회
DNS 조회를 통해 도메인명의 실제 IP 주소를 조회한다
* DNS 데이터를 조회할때 먼저 로컬 캐시를 조회하고 캐시에 없다면 DNS 서버에 재귀적으로 조회를 수행한다
###### 3. TCP 연결
대상 서버와 논리적 연결을 하기 위해 TCP프로토콜을 통해 3-way handshake 과정을 거친다.
HTTPS인경우 TLS handshake 과정을 추가적으로 거친다
###### 4. 웹 브라우저가 HTTP를 통한 페이지 요청
TCP 연결이되고 웹 브라우저는 HTTP 프로토콜을 따라 서버에게 페이지를 요청한다
###### 5. 웹 서버가 요청을 처리하고 응답을 전송
웹 서버는 웹 브라우저의 요청을 받아 처리를 하고 페이지를 응답으로 전송한다
###### 6. 웹 브라우저의 콘텐츠 렌더링
웹 브라우저는 받은 페이지를 통해 적절히 렌더링 과정을 수행한다
###### 참고
https://tjddndk17.github.io/info/web-browser-server
https://sunrise-min.tistory.com/entry/%EC%9B%B9-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%97%90-URL%EC%9D%84-%EC%9E%85%EB%A0%A5%ED%95%98%EA%B3%A0-%EC%82%AC%EC%9A%A9%EC%9E%90%EC%97%90%EA%B2%8C-%EB%B3%B4%EC%97%AC%EC%A3%BC%EA%B8%B0%EA%B9%8C%EC%A7%80-%EA%B3%BC%EC%A0%95