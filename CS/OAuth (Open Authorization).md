# OAuth
사용자의 로그인 정보를 직접 제공받지 않고도 내 서비스가 타 서비스 (Google, Naver, Kakao)의 사용자 정보와 기능에 대한 접근 권한을 안전하게 위임받게 해주는 표준 프로토콜
##### 실제 예시
EX) 비서(내 서비스)는 앞으로 거래처(타 서비스)의 거래 진행사항을 조회하기 위해 사장(사용자)에게 거래처 계약 인증서를 요구한다 사장은 거래처로 부터 거래처 계약 인증서를 받아 비서에게 전달하면서 계약 진행사항 조회 권한을 위임한다. 그리고 나중에 사장이 비서에게 계약 진행사항을 요청하면 비서는 인증서를 통해 거래처에게 진행사항을 요청하고 진행사항를 사장에게 보고한다.
## OAuth 요소
##### Resource Owner
타 서비스 정보를 가지고 있는 사용자, 클라이언트를 이용하는 사용자
##### Client
내 서비스
##### Authorization Server
권한을 부여 해주는 서버
**Resource Owner**는 ID, PW를 넘겨 로그인해 Authorication Code를 전달
**Client**는 Authorication Code를 전달해 Access Token, Refresh Token를 전달해 권한 위임
##### Resource Server
타 서비스 자원을 제공하는 서버(Google, Naver, Kakao)

Client는 Access Token을 넘겨야 타 서비스에 대한 사용자의 정보에 접근 할 수 있다
##### Authorication Code
Access Token 발급을 위한 인증코드

Accss Token이 발급되면 만료된다
##### Access Token
Resource Server 접근 토큰, Access Token을 통해 사용자로부터 권한이 위임되었음이 증명된다.
##### Refresh Token
Access Token 재발급 토큰

why?) Access Token은 보안상 유효기간이 짧아, 자주 재발급이 필요하다 짧은 주기로 재발급을 위해선 유저가 로그인하면 번거로워 Refresh Token을 통해 Access Token을 재 발급해 번거로움을 차단
### OAuth 서비스 등록 요소
##### Client ID
클라이언트 식별자
##### Client Secret
Client ID에 대한 비밀번호
외부에 노출 되면 안된다
##### Authorized redirect URLs
Authorization Server가 인증 코드를 사용자에게 전달하는 엔드포인트로, 인증 코드 요청 유효성 검사에도 사용되는데 인증 코드를 요청할 때 전달하는 redirect URL이 정확하게 일치 하지 않는다면 인증 코드를 전송하지 않는다.
##### Scope
리소스 서버에서 접근 할 수 있는 정보나 기능의 범위다, Authorization Server는 클라이언트에게 Scope 범위 내에서 권한을 위임한다
## 동작 과정
![[Pasted image 20250227054601.png]]
### 1, 2 서비스 접근 및 이용시도 
1. 사용자는 서비스 접근을 위해 구글 로그인 버튼을 누른다.
2. 구글 로그인 버튼에 서비스의 Client ID, Redirect_URL가 포함되어 있다.
### 3. 로그인 페이지 요청
1. 구글 로그인 버튼을 눌러 사용자(브라우저, 앱)는 Client ID, Redirect URL를 포함해 로그인 페이지를 요청한다.
### 4. 로그인 페이지 제공
1. 클라이언트 아이디와 리다이렉트 URL이 인증서버와 일치하는지 비교한다(유효성 검사)
2. 일치가 확인되었으면 인증 서버는 로그인 페이지로 이동시켜준다
### 5. ID/PW 입력
1. 사용자는 ID/PW를 적고 로그인이 성공하면, 인증 서버는 사용자에게 클라이언트에게 권한을 위임할 것인지 물어본다(유저의 동의)
2. 동의를 한다면 인증 서버에게 권한의 위임을 승인했다고 전달한다
### 6. Authorization code 발급
1. 인증서버는 인증코드를 리다이렉트 URL를 통해 전달한다.
### 7. Redirect_URL로 Authorization code 전달
1. 사용자는 인증코드를 리다이렉트 URL를 통해 클라이언트에게 전달한다
### 8. Authorization code로 Access Token 요청
1. 클라이언트는 인증코드와 함께 엑세스 토큰을 요청
### 9. Access Token 발급
1. 인증 서버는 엑세스 토큰을 발급해 클라이언트에게 전달한다(타 서비스 통의)
2. 엑세스 토큰이 발급되면서 인증 코드는 만료된다(일회용)
3. 이제 클라이언트는 권한을 정상적으로 위임 받았고 리소스 서버에 접근 권한이 생긴다.
### 10. 인증 완료 및 로그인 성공
1. 클라이언트는 엑세스 토큰 발급을 확인하고, 사용자에게 로그인이 완료되었음을 응답한다.
### 11. 서비스 요청
1. 사용자는 클라이언트에게 서비스를 요청한다(서비스를 이용하기 위해 타 서비스 접근이 필요한 경우 한정)
### 12. Access Token으로 API호출
1. 클라이언트는 Access Token을 통해 리소스 서버에 접근
### 13. Access Token 검증 및 서비스 제공
1. 엑세스 토큰을 통해 권한이 확인되고 서비스를 제공한다
### 14. 서비스 제공
1. 사용자가 요청한 서비스를 응답한다.

참고
https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-OAuth-20-%EA%B0%9C%EB%85%90-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#oauth_%EA%B5%AC%EC%84%B1_%EC%9A%94%EC%86%8C
https://hudi.blog/oauth-2.0/#5--6-Authorization-Code-%EB%B0%9C%EA%B8%89-Redirect-URI%EB%A1%9C-%EB%A6%AC%EB%94%94%EB%A0%89%ED%8A%B8
