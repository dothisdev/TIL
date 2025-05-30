---
tags: streaming
---
![[Pasted image 20250423004906.png]]
# RTMP(Real-Time Messaging Protocol)
RTMP는 비디오 스트리밍, TV 생방송등에 사용되는 프로토콜

고화질 비디오는 파일 크기가 크기 때문에 단순히 전송하기에는 시간이 오래 걸린다, 하지만 RTMP는 이러한 데이터를 작은 패킷으로 분할하여 빠르게 전송하고, 클라이언트에 다시 조합해 보여주는 방식

RTMP는 Flash Player를 지원하기 개발되었으며, 현재 Adobe Flash Player가 중단되면서 브라우저, IOS, 안드로이드 등에서 사용되지 않고 있으며, 업데이트 및  지원이 중단되었다

현재는 RTMP를 주로 SNS, 라이브 스트리밍 플랫폼, 미디어 서버에 인코딩된 영상을 전송하는데 사용된다.
## 특징
* 실시간 영상 전송 프로토콜
* 퍼스트 마일 전송용으로 적합
* 낮은 지연시간
* TCP 기반
* 지속적인 연결 유지
* Flash 기반으로 개발되어 현재 브라우저, IOS, 안드로이드같은 클라이언트 앱에서 사용할 수 없음
* 현재는 업데이트와 지원이 중단됨
## RTMP 스트리밍 방식
RTMP는 고화질 비디오 같은 큰 데이터를 작은 패킷으로 나눠 전송한 뒤 다시 재조립하는 방식으로 동작한다, 이 방식으로 **낮은 지연시간**을 얻을 수 있다.

그러나 현재는 RTMP를 지원하는곳이 적어지면서 RTMP는 주로 **퍼스트 마일 전송(First-Mile Delivery)** 에  사용된다 그리고 다른 구간은 HLS 같은 프로토콜을 함께 사용한다
e.g) OBS, Youtube Live등에서 퍼스트 마일 전송 목적으로 RTMP사용
> [!NOTE] 퍼스트 마일 전송
> 영상 데이터가 인코더에서 서버까지 전송하는 과정을 말한다

> [!NOTE] 인코더 역할
> 인코더는 영상 데이터를 코덱을 이용해 압축하고, RTMP 프로토콜을 사용하여 영상 데이터를 패킷으로 분할해 전송한다
###### 참고
https://restream.io/blog/rtmp-streaming/#rtmp-vs-http-streaming
https://www.wowza.com/blog/rtmp