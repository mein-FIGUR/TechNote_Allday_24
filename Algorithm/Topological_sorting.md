# Topological_sorting (위상 정렬)

- 순서가 정해져 있는 일련의 작업을 차례대로 수행해야 할 때 사용할 수 있는 알고리즘
- 대표적으로 '선수과목을 고려한 학습 순서 결정'을 하는 경우 쓰일 수 있다.



### ✔정의

---

- 방향 그래프의 모든 노드를 "방향성에 거스르지 않도록 순서대로 나열하는 것"



### 🔍진입차수(Indegree)

---

- 특정한 노드로 "들어오는" 간선의 개수

- 컴퓨터공학과의 커리큘럼을 예시로 들었을 때, '고급 알고리즘'과목은 '자료구조'와 '알고리즘'을 선수과목으로 들어야 수강할 수 있다면 '고급 알고리즘'의 진입차수는 2이다.

  ![진입차수](https://blog.kakaocdn.net/dn/lTmsq/btqSmzKHMo9/2SyfTqWekkJTtEZ0p1NuP0/img.png)

### 📌진행 방식

---

1. 진입차수가 0인 노드를 큐에 넣는다.

2. 큐가 빌 때까지 다음의 과정을 반복한다.

   a. 큐에서 원소를 꺼내 해당 노드에서 출발하는 간선을 그래프에서 제거한다.

   b. 새롭게 진입차수가 0이 된 노드를 큐에 넣는다.

   

- 이때 모든 원소를 방문하기 전에 큐가 빈다면 사이클이 존재. 사이클이 존재하는 경우 사이클에 포함되어 있는 원소 중에서 어떠한 원소도 큐에 들어가지 못하기 때문.

- 현재는 사이클이 없는 것을 가정하고 나중에 사이클이 있는 경우도 다뤄보자.



### 🖋코드

---

- 백준 2252번 줄 세우기 문제 풀이를 가져왔다.
- N명의 학생들을 키 순서대로 줄을 세우는데 모든 학생들의 키를 다 알고 있지 않다.
- 두 학생의 키를 비교한 정보가 있는데 몇몇 학생들의 정보만 있다.
  - 따라서 답이 여러 가지일 수 있다.

```python
# 백준 2252 줄 세우기

import sys
from collections import deque

input = sys.stdin.readline

def solution():
    # 노드의 개수와 간선의 개수 입력받기
    number_of_vertex, number_of_edge = map(int, input().rstrip().split())	
    # 모든 노드에 대한 진입차수는 0으로 초기화
    indegree = [0] * (number_of_vertex + 1)
    # 각 노드에 연결된 간선 정보를 담기 위한 그래프 초기화
    graph = [[] for _ in range(number_of_vertex + 1)]
    
    # 방향 그래프의 모든 간선 정보를 입력 받기
    for _ in range(number_of_edge):
        a, b = map(int, input().rstrip().split())
        graph[a].append(b)
        indegree[b] += 1

    # 위상 정렬 함수
    def topology_sort():
        nonlocal number_of_vertex
        result = []
        queue = deque()

        for i in range(1, number_of_vertex + 1):
            if indegree[i] == 0:
                queue.append(i)
		
        # 큐가 빌 때까지 반복
        while queue:
            now = queue.popleft()
            result.append(now)

            for i in graph[now]:
                indegree[i] -= 1
                if indegree[i] == 0:
                    queue.append(i)

        return result

    # 위상 정렬을 수행한 결과 출력
    result = topology_sort()
    for i in result:
        print(i, end=" ")

    return

solution()
```





## 참고자료

- "이것이 코딩테스트다"(나동빈저) 

- https://freedeveloper.tistory.com/390

