![[Pasted image 20250501183755.png]]
# MQTT(Message Queueing Telemetry Transport)란?
* Publish-Subscribe 기반 메시지 송수신 프로토콜
* MQTT구현에 필요한 코드량이 적고, 메시지 크기가 작아, 자원이 제한된 IoT혹은 대용량 트래픽 전송에 사용된다
	* Facebook Messenger에서 MQTT가 채택
* 메시지 크기가 작은만큼 유형과, QoS에 제약이 있다
	* 메시지 글자 수 제한이 없고, 긴 메시지나 JSON 포맷 또는 파일 전송은 가능
* 연결지향적
* IoT와 클라이언트간의 통신은 오로지 브로커를 통해서 이뤄진다
	* Iot ->Broker-> Client
* QoS(Quality of Service)를 통해 신뢰성 제어 가능
	* 0: 최대 1회 전송, 전송 보장X
	* 1: 최소 1회 전송, 메시지를 정해진 횟수만큼 전송하며, 가벼운 핸드셰이킹 과정을 엄밀한 추적을 하지않아 중복 가능성이 존재
	* 2: 메시지를 정확히 한 번 수신할 수 있도록 보장. 메시지 핸드셰이킹 과정을 엄밀히 추적, 신뢰성이 보장되지만 속도는 느려진다
	* QoS는 TCP, IP 프로토콜에 영향을 주지않는다
	* 0~1 정도의 QoS를 가지고 별도의 신뢰성 보장은 애플리케이션 차원에서 관리하는 방법을 주로 사용한다
![[Pasted image 20250501190042.png]]
## MQTT 구조
###### Topic
메시지의 subscribe, publish 대상 주제라고 생각하면된다.
###### 참고
https://underflow101.tistory.com/22