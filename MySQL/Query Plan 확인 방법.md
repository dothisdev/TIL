# Query Plan
[[TIL/MySQL/옵티마이저.md|옵티마이저]]가 동작하여 선정한 최적의 쿼리 실행 계획
## Query Plan 확인방법
```sql
EXPLAIN SELECT * FROM t1;
```
EXPLAIN을 쿼리의 접두어로 추가하여 쿼리 플랜을 확인할 수 있다

쿼리 플랜을 통해 쿼리가 어떻게 조인을 하는지, 인덱스는 어떤걸 사용하는지를 확인할 수 있고 그걸 기반으로 인덱스 추가, 인덱스 최적화를 통해 쿼리 최적화를 기대할 수 있다
### Query Plan 요소
- id : 쿼리 내의 select 문의 실행 순서
- select_type : select 문의 유형
	- SIMPLE: 단순 select ( union이나 서브쿼리를 사용하지 않음 )  
	- PRIMARY: 가장 외곽에 있는 select문  
	- UNION: union에서의 두번째 혹은 나중에 따라오는 select문  
	- DEPENDENT UNION: union에서의 두번째 혹은 나중에 따라오는 select문, 외곽 쿼리에 의존적이다.  
	- UNION RESULT: union의 결과물  
	- SUBQUERY: 서브쿼리의 첫번째 select  
	- DEPENDENT SUBQUERY: 서브쿼리의 첫번째 select, 바깥 쪽 쿼리에 의존적이다.  
	- DERIVED: from절의 서브쿼리
- table : 참조하고 있는 테이블명
- partitions : 매칭되는 파티션
- type : 조인타입이며 쿼리 성능과 아주 밀접한 항목, 아래로 갈수록 성능이 낮아짐
	1. system : 테이블에 단 하나의 행만 존재(=시스템 테이블). const 조인의 특별한 형태이다.  
	2. const : 하나의 매치되는 행만 존재하는 경우. 하나의 행이기 때문에 상수로 간주되며, 한번만 읽어들이기 때문에 무척 빠르다.  
	3. eq_ref : 조인수행을 위해 각 테이블에서 하나의 행만이 읽혀지는 형태. const 타입 외에 가장 훌륭한 조인타입이다.  
	4. ref : ref조인에서 키의 가장 왼쪽 접두사 만 사용하거나 키가 a PRIMARY KEY또는 UNIQUE인덱스 가 아닌 경우 (즉, 조인이 키 값을 기반으로 단일 행을 선택할 수없는 경우) 사용된다. 사용되는 키가 몇 개의 행과 만 일치하는 경우 이는 좋은 조인 유형이다.  
	5. fulltext : fulltext 색인을 사용하여 수행된다.  
	6. ref_or_null : 이 조인 유형은 비슷 ref하지만 MySQL이 NULL값 을 포함하는 행을 추가로 검색한다는 점이 다르다. 이 조인 유형 최적화는 하위 쿼리를 해결하는 데 가장 자주 사용된다.  
	7. index_merge : 인덱스 병합 최적화가 적용되는 조인타입. 이 경우, key컬럼은 사용된 인덱스의 리스트를 나타내며 key_len 컬럼은 사용된 인덱스중 가장 긴 key명을 나타낸다.  
	8. range : 인덱스를 사용하여 주어진 범위 내의 행들만 추출된다. key 컬럼은 사용된 인덱스를 나타내고 key_len은 사용된 가장 긴 key부분을 나타낸다. ref 컬럼은 이 타입의 조인에서 NULL 이다. range 타입은 키 컬럼이 상수와 =, <>, >, >=, <, <=, IS NULL, <=>, BETWEEN 또는 IN 연산에 사용될때 적용된다.  
	9. index : 이 타입은 인덱스가 스캔되는걸 제외하면 ALL과 같다. 보통 인덱스 파일이 데이터 파일보다 작기 때문에 ALL보다 빠르다.  
	10. ALL : 이전 테이블과의 조인을 위해 풀스캔이 된다. 만약 조인에 쓰인 첫 테이블이 고정이 아니라면 비효율적이다. 그리고 대부분의 경우 아주 느리며, 보통 상수값이나 상수인 컬럼값으로 row를 추출하도록 인덱스를 추가하여 ALL 타입을 피할 수 있다.
- possible_keys : MySQL이 해당 테이블의 검색에 사용할 수 있는 인덱스들
- key : MySQL이 실제 사용한 key나 인덱스
- key_len : MySQL이 사용한 인덱스의 길이, key 컬럼의 값이 NULL이면 이 컬럼의 값도 NULL
- ref : 행을 추출하는 데 키와 함께 사용 된 컬럼이나 상수값
- rows : 이 값은 쿼리 수행에서 MySQL이 찾아야하는 데이터행 수의 예상값. 추정 수치이며 항상 정확하지 않다.
- filtered : filetered열에 나타난 조건에 의해 필터링 될 테이블 행의 예상 비율을 나타낸다. 즉 rows는 검사 된 행 수를 나타내고 rows * filtered / 100은 이전 테이블과 조인 될 행 수를 표시
- Extra : MySQL이 이 쿼리를 어떻게 해석하는 지에 대한 추가 정보 
	- distinct : 이미 처리한 값과 동일한 값을 가진 Row는 처리하지 않음.
	- not exist : left join을 수행함에 매치되는 한 행을 찾으면 더 이상 매치되는 행을 검색하지 않음.
	- Range checked for each record :사용할 좋은 인덱스가 없음.
	- using filesort : 정렬을 위해 추가적인 과정을 필요로 함(물리적인 정렬작업 수행)
	- using index : 실제 데이터 Block을 읽지 않고 인덱스 Block 만으로 결과를 생성할 수 있는 경우
	- using temporary : 임시 테이블을 사용. order by 나 group by 절이 각기 다른 컬럼을 사용할 때 발생
	- using where : where절이 다음 조인에 사용될 행이나 클라이언트에게 돌려질 행을 제한하는 경우
	- using index for group-by



###### 참고
https://ibks-platform.tistory.com/374
https://spidyweb.tistory.com/460
