![[Pasted image 20250501150617.png]]
# gRPC란?
gRPC는 구글에서 개발한 최적화 기능과 함께 RPC를 구현한 RPC 프레임워크다
* **gRPC를 통해 클라이언트는 다른 언어(gRPC가 지원하는)로 작성된 서버의 함수를 호출 할 수 있다는 점**을 통해 분산 응용프로그램 및 서비스 작성이 쉬워진다
* HTTP 2.0, IDL로 protocol buffer를 사용한다
* SSL/TLS 암호화를 사용한다
### RPC(Remote Procedure Call)란?
RPC는 클라이언트가 특정 서버(물리적으로 떨어져 있는)의 함수를 직접 혹은 간접적으로 호출 할 수 있게 해주는 프로토콜이다. 

클라이언트는 서버의 프로세스로 요청을 하며, 프로세스는 클라이언트의 원격 호출을 수신 대기 상태로 항상 유지를 한다. 클라이언트의 요청에는 호출할 함수, 파라미터가 포함되었으며, 기반 프로토콜은 HTTP, TCP, UDP를 통해 이뤄진다

## Protocol Buffer란?
Protocol Buffer는 IDL과 데이터 직렬화 프로토콜로서 사용된다.

다른 IDL인 XML, JSON 보다 데이터 직렬화에 있어 속도가 빠르고 크기도 적고 가독성이 좋은 장점이 있다
###### message 정의
.proto파일을 통해 Protocol Buffer를 통해 직렬화 하려는 메시지 구조를 정의 할 수 있다
```proto
message Person{
	string name = 1;
	int32 id = 2;
	bool has_ponycopter = 3;
}
```
프로토콜 버퍼 컴파일러인 Protoc를 사용하면 메시지에 대해 프로퍼티 제어, 직렬화/역직렬화 기능이 포함된 클래스를 자동으로 생성된다
###### service 정의
```proto
// The greeter service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply) {}
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings
message HelloReply {
  string message = 1;
}
```
protoc 컴파일러와 gRPC 플러그인을 함께 사용한다면 클라이언트/서버 코드가 자동으로 생성되고 message 지원 코드도 또한 생성된다
###### 참고
https://grpc.io/docs/what-is-grpc/introduction/
https://leeseojune53.tistory.com/28