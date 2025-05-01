---
aliases:
  - HLS/DASH 프로토콜
tags:
  - streaming
---
# HTTP live streaming(HLS) 란?
* HLS는 비디오 스트리밍에 특화된 프로토콜이다.
* HLS는 스트리밍밍, 라이브 스트리밍에 주로 사용된다
* HLS는 비디오 파일을 여러개의 HTTP파일로 나누고 HTTP 프로토콜을 통해 클라이언트에게 전송한다 그리고 클라이언트는 나눠진 HTTP파일을 다시 동영상 형태로 되돌린다
* HLS는 HTTP 기반으로 동작하기 때문에 쉽게 통신가능하다,
  why?) 웹 서버와 웹 브라우저또한 HTTP를 기반으로 동작하기 때문 특별한 환경이 필요하지않음
* HLS는 네트워크 상태가 떨어져도 비디오 재생을 멈추지 않도록 네트워크 상태에 맞는 비디오 화질로 전환이 가능하다(Adaptive bitrate streaming)
* HLS는 애플 제품을 지원하기 위해 만들어진 프로토콜이다, 그러나 다른 모든 기기에서도 사용되고 있다
## HLS 동작과정
1. **Encoding**: 클라이언트가 재생 할 수 있게 비디오 데이터를 인코딩 되는 과정, HLS은 H.264 or H.265 인코딩을 사용해야한다
2. **Segmenting**: 비디오를 segment로 나눈다, segment에는 몇 초 정도 길이의 비디오를 저장하고 있음(기본 길이 : 6초)
	1. segment의 순서를 기록하기 위해 index 파일을 생성함
	2. 다양한 화질의(480p, 720p, 1080p 등) segment를 생성함
3. **Distribution**: 인코딩된 비디오 segment를 클라이언틔 요청에 의해 전송
4. **클라이언트**: 클라이언트는 전송된 segment를 index에 맞춰 순서를 맞추고 네트워크 상태에 맞는 화질로 동영상을 재생한다
## HLS가 UDP가 아닌 TCP를 표준으로 둔 이유
1. HLS는 HTTP를 사용하고 HTTP는 TCP를 표준으로 사용하기 때문
2. 현재의 네트워크 인프라는 충분히 빠른 대역폭을 지원하기 때문에 TCP를 사용해도 충분히 실시간으로 높은 화질의 비디오가 제공 되기 때문
3. Adaptive bitrate streaming로 대역폭에 맞춰 맞는 화질을 제공할 수 있기 때문
4. 스트리밍은 몇 초 지연돼도 문제가 안되기 때문
###### 참고
https://www.cloudflare.com/ko-kr/learning/video/what-is-http-live-streaming/