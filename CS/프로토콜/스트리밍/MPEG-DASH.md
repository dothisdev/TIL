---
tags:
  - streaming
---
# DASH(Dynamic Adaptive Streaming Over HTTP)란?
* DASH는 스트리밍에 사용되는 프로토콜로 HTTP에 기반한다
* HTTP 프로토콜 기반이기 때문에 추가적인 설정이 필요하지 않다
* 비디오를 segment로 나누고, 네트워크 상태에 따른 화질을 제공하는 점이 HLS 방식과 비슷하다
* TCP 기반
* 인코딩에 표준에 제약이 없다(HLS는 H.264 or H.265만 허용)
* APPLE 제품에 지원하지 못한다(HLS만 허용)
* 국제 표준으로 지정된 스트리밍 프로토콜(HLS는 비표준 BUT 많이 사용하는 프로토콜)
## MPEG-DASH 과정
1. **인코딩 및 조각화**
   서버는 비디오를 여러 segment 조각으로 나누고, segment를 인코딩
	1. 인코딩 표준에 제약이 없음
	2. segment 조각에는 몇 초 길이의 비디오가 저장됨
	3. segment로 나누면서 segment 순서가 기록된 index 파일 생성
2. **전송**
   클라이언트 요청에 의해 서버는 사용자에게 지속적으로 인코딩 된 segment를 전송
3. **디코딩 및 재생**
   클라이언트는 전달 받은 segment를 다시 비디오로 디코드하고 재생함
	1. 네트워크 상태에 맞춰 적절한 화질로 영상을 (비디오 중단 없이)재생한다
###### 참고
https://www.cloudflare.com/ko-kr/learning/video/what-is-mpeg-dash/