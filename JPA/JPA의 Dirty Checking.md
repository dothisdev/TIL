# Dirty Checking
JPA가 영속 엔티티의 변경을 감지할때 사용하는 변경 감지 기능
Why?) 변경된 엔티티 내용을 자동으로 DB에 반영하기 위해
### 특징
* 영속성 엔티티를 대상으로 체크
* 최초로 영속상태가 되었을때 엔티티를 스냅샷으로 저장
* flush() 호출 시점에 현재 엔티티와 스냅샷을 비교하여 변경 감지
###### 예시
멤버 엔티티를 영속 컨텍스트로 가져오면서 스냅샷 생성 -> 멤버 엔티티 이메일 변경 -> flush() -> 현재 멤버 엔티티와 스냅샷 비교 -> 이메일 변경 감지
###### 실생활 예시
공항 보안 검색 : 입국 할때 얼굴 사진을 촬영 -> 출국 할때 입국할때 찍은 얼굴 사진을 비교하여 차이 감지

[[TIL/자바 ORM 표준 JPA 프로그래밍/3장 영속성 관리#4. 변경 감지|변경 감지]]
