# Kruskal Algorithm

- 최소 비용 신장 부분 트리를 찾는 알고리즘
- 그래프의 모든 정점들을 최소의 비용으로 연결하기 위해 사용
- Greedy 알고리즘 기반



### ✔시간 복잡도

---

- 간선의 개수 `E`, 정점의 개수 `V`를 기준으로, `O(ElogV)`의 시간복잡도를 가지고 있다.



### 🔍신장 트리와 MST

---

- 신장 트리(Spanning Tree)

> 신장 트리(Spanning Tree)는 그래프 내의 모든 정점을 포함하고, 사이클이 없는 그래프를 말합니다.
>
> n개의 정점(Vertex)가 있다면, 신장 트리의 간선(Edge) 수는 n-1이 됩니다.

- MST(Minimum Spanning Tree)

> 최소 신장 트리(Minimum Spanning Tree)는 각 간선이 가지고 있는 가중치의 합이 최소가 되는 신장 트리를 말합니다.



### 📌진행 방식

---

- 그래프의 간선들로 이루어진 리스트가 있다고 가정
- 그래프 간선들의 가중치를 **오름차순**으로 정렬, 가중치가 가장 적은 간선부터 탐색



1. 가장 작은 가중치의 간선을 리스트에서 빼냄
2. 해당 간선이 어떤 두 트리를 연결한다면, 합쳐서 하나의 트리로 바꿈(**Union & Find**)
3. (2)의 조건을 만족하지 않는다면, 버림



- 위의 1~3의 과정을 진행하면서, n 개의 정점 기준 n-1 개의 간선이 남게 된다.

![KruskalDemo](https://user-images.githubusercontent.com/44635266/66712118-cf661680-edd2-11e9-952c-b043e2bcdb8a.gif)





## 🖋Code

- 코드는 [프로그래머스: 섬 연결하기](https://programmers.co.kr/learn/courses/30/lessons/42861) 문제를 따왔다.
  - MST를 찾고, 그때의 모든 가중치의 합을 구하는 문제
- `cost`인 가중치를 작은 값 기준으로 정렬
- 부모 노드를 설정하는 `parent` 리스트
  - 초기 값은 본인으로 설정
- `union` 함수와 `find` 함수를 통해 **Union&Find** 구현
  - Union: 서로 다른 두 트리를 합치는 함수(루트 노드를 하나로 설정)
  - Find: 해당 노드의 루트 노드를 찾는 함수
- 간선에서의 두 노드의 루트 노드가 다른 경우, 하나의 트리로 합치고, 해당 가중치를 추가

```python
def solution(n, costs):
    answer = 0
    parent = [i for i in range(n)] # 부모 노드를 설정하기 위한 리스트
    costs.sort(key=lambda x:x[2]) # cost가 작은 값 기준으로 정렬

    def find(a): # 루트 노드를 찾는 함수
        if parent[a] == a: # 본인이 루트 노드인 경우
            return a
        parent[a] = find(parent[a])
        return parent[a] # 루트노드를 찾아 저장하고 리턴

    def union(a, b): # Tree 두개를 합치는 과정
        pa, pb = find(a), find(b) # 각 노드의 루트 노드
        if pa == pb : # 루트 노드가 같다는 것은 같은 트리
            return
        elif pa < pb : # 노드값이 더 낮은 트리쪽으로 합침
            parent[pb] = pa
        else :
            parent[pa] = pb
        return   

    for n1, n2, c in costs:
        if find(n1) != find(n2): # 루트 노드가 다르면 연결 후 경로 값 추가
            union(n1, n2)
            answer += c

    return answer
```



