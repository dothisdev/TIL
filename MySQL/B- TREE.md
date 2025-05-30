# B- TREE
![[Pasted image 20250320231135.png]]
자식을 2개만 갖는 Binary Tree의 확장 구조로 **2개이상의 자식과 키를 갖을 수 있는 Tree 구조**

많은 자식노드와 많은 키를 가질 수 있는 구조로 **트리의 높이를 크게 줄여, 디스크 접근 횟수를 줄이고 데이터 검색과 업데이트를 더 빠르게 할 수 있다**.
B- TREE는 항상 균형잡힌 구조를 유지하여, 검색, 삽입, 삭제와 같은 작업이 어떤 노드든 일관적인 효율로 처리된다
## 구조
* Root Node: 최상단에 있는 노드
* Branch Node: 중앙에 있는 노드
* Leaf Node: 최하단에 있는 노드
## 규칙
m은 차수라고도 부른다
* m: 최대 가질 수 있는 자식 수
* m-1: 최대 가질 수 있는 키 수
1. B- TREE의 모든 리프 노드는 같은 높이에 있다.  어떤 리프 노드는 더 낮거나 높을 수 없다
2. B- TREE의 각 노드의 키는 오름차순으로 저장되어야 한다
3. B- TREE에서의 비-리프 노드(루트 노드 제외)는 최소 m/2개의 자식을 가져야 한다
4. 모든 노드(루트 노드 제외)는 최소 (m/2)-1개의 키를 가져야 한다
5. 루트 노드가 리프 노드인경우(트리에 유일한 노드인 경우) 자식이 없고 최소 1개의 키를 갖고 있어야 한다, 루트 노드가 비-리프노드인경우 최소 2개의 자식과 최소 하나의 키를 갖는다
6. m-1개의 키 값을 가진 비-리프 노드는 m개의 비어있지 않은 자식을 가져야 한다
## B- TREE 검색
B- TREE 검색은 Binary Tree와 비슷하다
e.g) k를 검색할때
1. Root Node에서 시작해 재귀적으로 아래를 검색
2. 모든 비-리프 노드
	1. 현재 노드가 k를 포함하면 노드를 반환
	2. 노드에 k가 포함되지 않는다면 K와 같거나 K보다 크지만 가장 근접한 키를 가진 자식노드를 찾는다
3. 리프노드에 달성할때 까지 k를 찾지 못하면 NULL를 반환
### B- TREE 장점
* 삽입, 삭제, 검색과 같은 기본 연산이 빠르고 보장된 시간 복잡도O(log n)를 가짐
* 균형을 유지
* 디스크 접근 횟수를 줄임
	* 트리의 높이를 줄여주기 때문
* 높은 동시성과 처리량을 제공
	* 트리의 높이를 줄이고 수용하는 키를 늘려  디스크 I/O가 최적화 되어 더 빠른 처리 가능
* 효율 적인 저장공간 활용 가능
	* 하나의 노드가 여러 키를 가지기 때문
###### 참고
https://www.geeksforgeeks.org/introduction-of-b-tree-2/
https://fierycoding.tistory.com/78