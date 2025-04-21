![IP 라우팅 다이어그램](https://cf-assets.www.cloudflare.com/slt3lc6tev37/5biqo5wm6nM8GSmiNyiAnl/b6b5c9befeda6ba99b4380d84953de18/routing-diagram.svg)
# IP 프로토콜
IP 프로토콜은 3계층에 위치하며 패킷을 IP Adress와 Routing을 통해 정확한 위치에 빠르게 보내줄 수 있도록 해준다.
데이터를 패킷이라는 작은 단위로 나누어 전송하고, 각 패킷에는 IP 주소를 포함한 헤더와 페이로드가 구성되어 있다.

IP 프로토콜은 대신 비연결성이고 비신뢰성 성질을 가지고 있다.
![[internet_protocol_ip_address_diagram.svg]]
###### IP 주소
인터넷에 연결하는 장치나 도메인에 할당된 고유 식별자를 말한다, IP 프로토콜이 보낼 주소로 지정하는 대상이다

> [!NOTE] IPv4, IPv6
> IPv4: 32비트 주소 체계로, 현재는 거의 고갈상태
> IPv6: 128비트 주소 체계로, 많은 경우의 수를 제공하지만 아직 보편화 되지는 않음
###### IP 패킷
IP 패킷은 데이터 패킷에 IP헤더가 추가된 형태, IP 헤더는 바이너리 데이터이며, 여러 정보가 기록됨
- 헤더 길이
- 패킷 길이
- [Time To Live(TTL)](https://www.cloudflare.com/learning/cdn/glossary/time-to-live-ttl/), 즉 패킷이 삭제되기 전에 만들 수 있는 네트워크 홉 수
- 사용 중인 전송 프로토콜(TCP, UDP 등)
IPv4 헤더에는 총 14개의 정보 필드가 있지만, 그 중 하나는 선택 사항
###### IP Routing
인터넷은 특정 IP 주소 블록(IP Adress Block)을 담당하는 상호 연결된 대규모 네트워크로 구성 되어있으며,
대규모 네트워크를 AS(Autonomous System, 자율 시스템)라고 부른다.
라우팅 프로토콜(BGP등)은 목적지 IP 주소를 기반으로 AS간 패킷을 라우팅한다
라우터는 라우팅 테이블을 사용해 가장 효율적인 경로에 패킷을 전달한다, 패킷은 이런 과정을 거치며 여러 AS를 거치고 최종 목적지에 도착. 

또한 패킷은 여러 경로가 존재한다면, 서로 다른 경로로 이동해 같은 목적지에 도착할 수 있다



![[protocol_headers.svg]]
패킷은 여러 계층을 거치며 페킷 헤더를 덧붙힌다

###### 참고