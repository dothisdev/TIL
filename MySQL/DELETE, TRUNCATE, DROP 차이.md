
![[Pasted image 20250318205046.png]]
## DELETE
* 데이터를 1건씩 일일이 제거하는 방식
* 1건씩 일일히 제거해 처리속도가 느림
* WHERE 절을 사용하여 원하는 데이터를 제거할 수 있다
* 데이터가 저장되어 있는 Storage는 Release 되지 않음
* DELETE된 데이터는 ROLLBACK으로 되돌릴 수 있음
```sql
DELETE FROM dbtable WHERE {조건};
ROLLBACK;
COMMIT;
```
## TRUNCATE
* 전체 데이터를 제거하는 방식
* 전체적으로 제거해 처리속도가 빠름
* 최초 테이블이 생성된 상태로 만듬
	* 최초 생성 당시 Storage는 유지하고, 데이터가 담겨있던 Stroage는 Release
* 자동 COMMIT으로 ROLLBACK으로 되돌릴 수 없음
```sql
TRUNCATE TABLE dbtable;
```
## DROP
* 전체 데이터를 제거하는 방식
* 전체적으로 제거해 처리속도가 빠름
* 테이블이 아예 존재하지 않는 상태로 만듬
	* 테이블 자체를 제거하고, 생성된 모든 인덱스도 함께 제거
* 자동 COMMIT으로 ROLLBACK으로 되돌릴 수 없음
```sql
DROP TABLE dbtable;
```

|             | DELETE            | TRUNCATE        | DROP   |
| ----------- | ----------------- | --------------- | ------ |
| 명령어 종류      | DML               | DDL             | DDL    |
| 속도          | 느림                | 빠름              | 빠름     |
| 제거 범위       | 테이블에 저장된 데이터(0~N) | 테이블에 저장된 데이터 전체 | 테이블 자체 |
| AUTO COMMIT | NO                | YES             | YES    |
| ROLLBACK 가능 | YES               | NO              | NO     |

###### 참고
https://prinha.tistory.com/entry/SQL-DELETE-TRUNCATE-DROP-%EC%B0%A8%EC%9D%B4%EC%A0%90
https://lee-mandu.tistory.com/476