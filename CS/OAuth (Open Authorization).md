# OAuth
사용자의 로그인 정보를 직접 제공받지 않고도 내 서비스가 타 서비스 (Google, Naver, Kakao)의 사용자 정보와 기능에 대한 접근 권한을 안전하게 위임받게 해주는 표준 프로토콜
##### 실제 예시
EX) 사장(사용자)은 비서(내 서비스)에게 거래처(타 서비스) 계약 인증서 전달하면서 계약 진행사항 조회 권한을 위임한다. 그리고 나중에 사장이 비서에게 계약 진행사항을 요청하면 비서는 인증서를 통해 거래처에게 진행사항을 요청하고 결과를 사장에게 보고한다.
## OAuth 요소
##### Resource Owner
타 서비스 정보를 가지고 있는 사용자
##### Client
내 서비스
##### Authorization Server
Access Token 발급 서버
##### Resource Server
타 서비스 자원을 제공하는 서버
##### Authorication Code
Access Token 발급을 위한 인증코드
##### Access Token
타 서비스 엑세스 토큰
##### Refresh Token
Access Token 재발급 토큰

TOSTUDY
동작 과정, OAuth 요소 디테일
