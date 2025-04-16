![[Pasted image 20250416202405.png]]
URI는 URL, URN을 포함하고있다
그리고 다음과 같이 간단하게 나타날 수 있다
* URI - 자원의 식별자
* URL - 자원의 위치
* URN - 자원의 이름

> [!NOTE] 자원
> 자원이란 웹사이트 뿐만 아니라 json 데이터 pdf 등등 구분지을 수 있는 모든 데이터를 말한다

# URI(Uniform Resource Identifier)
* 인터넷의 자원 식별 표준 규약
* URI는 인터넷의 기본 조건으로 모든 프로토콜에 사용된다
* URI의 하위 개념인 URL, URN이 존재한다
# [[TIL/CS/URL의 구성.md|URL(Uniform Resource Locator)]]
* 인터넷의 자원 위치를 나타내는 표준 규약
* URL의 요소에 프로토콜이 포함되어 있다
e.g) 
* `http://example.com/mypage.html`
- `ftp://example.com/download.zip`
- `mailto:user@example.com`
- `file:///home/user/file.txt`
- `tel:1-888-555-5555`
- `http://example.com/resource?foo=bar#fragment`
# URN(Uniform Resource Name)
* 인터넷 자원 이름을 나타내는 표준 규약
e.g) urn:isbn:0451450523
# URI VS URL
URL과 URI의 차이에 대한 중요한 포인트는 다음과 같다
* 모든 URL은 URI다
* URL은 프로토콜과 host(port 해당안됨)를 필수로 포함시켜야한다
예를들어 `google.com`이 있다 이 표현은 URI가 맞지만 URL은 아니다
이유는 프로토콜이 포함되어 있지 않아 정확한 자원 위치를 알 수 없기 때문이다.
URL이 되려면 프로토콜을 포함해 정확한 자원위치를 명시해야 한다 `https://google.com`

즉 URI은 자원의 식별 표현, URL은 자원의 정확한 위치 표현이라고 차이를 둘 수 있다.
### 참고
https://stackoverflow.com/questions/176264/what-is-the-difference-between-a-uri-a-url-and-a-urn
https://inpa.tistory.com/entry/WEB-%F0%9F%8C%90-URL-URI-%EC%B0%A8%EC%9D%B4

