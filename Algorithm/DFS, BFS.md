### DFS
Deepth-First Search로 깊이를 우선으로 탐색하는 알고리즘이다.
스택 자료구조를 사용하고, 재귀 함수를 이용해 탐색한다

그래프 탐색을 예로들면
1. 탐색 노드를 스택에 삽입하고, 방문 처리한다
2. 스택의 최상단 노드에 방문하지 않은 인접 노드가 있다면 똑같이 스택 최상단에 삽입하고 방문 처리한다.
3. 스택의 최상단 노드에 방문하지 않은 인접 노드가 없다면 스택 최상단 노드를 꺼낸다
4. 1~3을 더이상 수행할 수 없을때 까지 반복
### BFS
Breath First Search로 너비를 우선으로 탐색하는 알고리즘이다.
큐 자료구조를 이용해 탐색한다

그래프 탐색을 예로들면
1. 탐색 노드를 큐에 삽입하고, 방문 처리한다
2. 큐에서 노드를 꺼내고, 해당 노드에 인접한 방문하지 않은 노드들을 방문 처리하고 삽입한다.
3. 2 과정을 더이상 수행할 수 없을때 까지 반복