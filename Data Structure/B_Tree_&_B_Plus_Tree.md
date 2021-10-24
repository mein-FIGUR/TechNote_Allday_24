# B Tree & B+ Tree

<br>

- B Tree❓
- B Tree의 규칙🔍
- B+ Tree❓

<br>

<br>

## B Tree❓

> 데이터베이스와 파일 시스템에서 널리 사용되는 트리 자료구조의 일종으로, 이진 트리를 확장해 **하나의 노드가 가질 수 있는 자식 노드의 최대 숫자가 2보다 큰 트리구조**이다. M개의 자식을 가질 수 있도록 설계된 경우, M차 B 트리라고 한다. 단순하고 효율적이며, 레벨로 따지면 완전히 균형을 갖춘 트리이다.

- 자식 수에 대한 일반화를 진행하면서, 하나의 레벨에 더 저장되는 것 뿐만 아니라 트리의 균형을 자동으로 맞춰주는 로직도 존재
- 탐색 시간이 무조건 `O(logN)`

![image](https://kookyungmin.github.io/image/DataStruc_img/DataStruc_img20.png)

<br>

<br>

## B Tree의 규칙🔍

- 각 노드의 자료수가 N이면, 자식수는 N+1이어야 한다.
- 각 노드의 data는 정렬된 상태여야 한다.
- 루트 노드는 적어도 2개 이상의 자식을 가져야 한다.
- 루트 노드를 제외한 모든 노드는 적어도 M/2개의 자료를 가지고 있어야 한다.
- 외부 노드로 가는 경로의 길이는 모두 같다.
- 입력 자료는 중복될 수 없다.

<br>

<br>

## B+ Tree❓

> B+ Tree(Quaternary Tree)는 키에 의해서 각각 식별되는 레코드(data node)의 효율적인 삽입, 검색과 삭제를 통해 정렬된 데이터를 표현하기 위한 트리자료구조의 일종이다. B 트리와 대조적으로 B+ 트리는 모든 레코드들이 트리의 가장 하위레벨에 정렬되어 있다.

- Index node, Data node 로 구성이 되어있다.
  - Index node: leaf 노드를 제외한 나머지 node
  - Data node: leaf node로, data node들은 linked list형태로 서로 연결되어 있고, 이를 순차집합(Sequence set)이라고 하며, 오름차순으로 정렬이 되어 있다.

![image](https://kookyungmin.github.io/image/DataStruc_img/DataStruc_img21.png)

<br>

<br>

### REFERENCE

- [[자료구조] 1. B-tree](https://kookyungmin.github.io/study/2018/07/28/data_structure_01/)
- [[자료구조] 2.B+-tree](https://kookyungmin.github.io/study/2018/07/29/data_structure_02/)
- [B 트리](https://ko.wikipedia.org/wiki/B_%ED%8A%B8%EB%A6%AC)
- [B+ 트리](https://ko.wikipedia.org/wiki/B%2B_%ED%8A%B8%EB%A6%AC)
- [[2020.10.25] 데이터베이스 인덱스는 왜 'B-Tree'를 선택하였는가](https://helloinyong.tistory.com/296)

