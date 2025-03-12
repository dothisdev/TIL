SQL Injection은 사용자 입력 유효성 검사가 미흡한 웹 앱에서 악의적인 SQL를 삽입하는 보안 취약점이다.

SQL Injection을 통해 인증을 우회하거나 정보를 조작할 수 있게된다.

e.g) 로그인 폼이 존재하고 로그인을 할때 다음과 같은 쿼리가 실행됨
```
"SELECT Count(*) FROM Users WHERE Username=' " + txt.User.Text+" ' AND Password=' "+ txt.Password.Text+" ' ";
```
해커는 다음과 같이 입력 password = **_anything 'or'1'='1_** 
```
"SELECT Count(*) FROM Users WHERE Username=' admin ' AND Password=' anything 'or'1'='1 ' ";
```
비밀번호는 false지만 '1'='1'은 true가 되어 결과적으로 true가 되면서 인증 우회가 성공
https://developer.mozilla.org/ko/docs/Glossary/SQL_Injection#%EC%9E%91%EB%8F%99_%EB%B0%A9%EC%8B%9D
### 예방방법
1. Prepared Statement 사용
	1. 준비된(분석이 완료된) Statement를 사용하여 값을 바인딩 했을 때 값이 SQL 형태라도 단순히 문자열로 처리되어 SQL Injection 예방 가능
2. 허용되지 않는 값 필터링
3. 특수 문자 이스케이프