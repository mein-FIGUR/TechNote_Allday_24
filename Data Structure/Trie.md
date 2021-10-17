# Trie

<br>

- Trie❓



<br>

## Trie❓

> 입력되는 문자열을 트리 형식으로 만들어 보다 빠르게 문자열 검색을 가능하게 한 자료구조로, radix tree, 또는 prefix tree라고도 한다.
>
> 문자열을 검색할 때, 문자열이 많을 경우 자주 사용되며, 시간복잡도가 빠르기 때문에 검색엔진 사이트에서 제공하는 자동 완성 및 검색어 추천 기능에서도 사용되는 경우가 있다. 하지만, 각 노드에서 자식들에 대한 포인터들을 배열로 모두 저장하고 있다는 점에서 저장 공간의 크기가 크다는 단점도 존재한다.

![img](https://camo.githubusercontent.com/7024b55e64516062054e9b5bccf35dc72d5e7a4cca88c8f57810804b955cb849/68747470733a2f2f74312e6461756d63646e2e6e65742f6366696c652f746973746f72792f323433353445333335383333413743463137)

- Tree 구조로 이루어져 있다.
- root 노드는 비어있다.
- 문자열의 끝을 알리는 flag가 존재

<br>

### 시간 복잡도⏱

- 문자열의 길이가 `m`이라고 하였을 때, `O(m)`의 시간 복잡도를 가진다.

<br>

<br>

## Code in Python🖋

- 클래스 `Node`, `Trie`가 필요
- `Node`는 `key`, `data`, `children`으로 이루어져 있음
  - `key`: 현재 노드가 가지고 있는 문자
  - `data`: 문자열이 끝난 경우, 해당 문자열을 `data`에 기록
    - default값으로 None을 가지고 있음
  - `children`: 자식 노드들이 저장되는 딕셔너리
    - key는 문자, value는 해당 문자를 key로 가진 노드
- `Trie`는 `head`만 가지고 있으며, `insert`, `search`함수가 기본적으로 존재
  - `head`는 루트 노드를 의미
  - `insert`: `word`를 추가하는 함수, 각 문자열을 하나씩 확인하며, 없는 경우 새로운 노드를 연결하여 추가하는 방식, 마지막 노드의 `data`에 `word`를 저장
  - `search`: `Trie`에 해당 `word`가 존재하는 지 유무를 확인, 각 문자를 하나씩 탐색하며 끝까지 도달한 후, 해당 노드의 `data`에 `word`가 저장된 경우만 `True`로 반환

```python
class Node:
    def __init__(self, key, data=None):
        self.key = key # 현재 노드의 문자
        self.data = data # 단어가 끝나는 경우, 해당 단어를 data에 저장
        self.children = {} # 자식 노드들이 저장되는 딕셔너리, key는 문자, value는 노드


class Trie:
    def __init__(self):
        self.head = Node(None) # 루트 노드

    def insert(self, word): # 단어 추가용 함수
        current = self.head

        for w in word:
            if w not in current.children: # 해당 문자열이 없는 경우, 노드 생성 후 자식에 추가
                current.children[w] = Node(w)
            current = current.children[w] # 자식 노드로 이동
        current.data = word # 마지막 노드에 데이터 저장

    def search(self, word): # 단어 탐색용 함수
        current = self.head

        for w in word:
            if w in current.children: # 자식에 문자열이 있는 경우, 자식노드로 이동
                current = current.children[w]
            else: # 없는 경우, 단어가 없으므로 False
                return False

        if current.data: # 데이터가 저장되어 있는 경우에만 단어가 존재
            return True
        else: # 데이터가 저장되어 있지 않으면, 마지막 노드가 아니므로 False
            return False

```

<br>

### Test

```python
trie = Trie()
words = ['cart', 'cow', 'call', 'cartoon']
for word in words:
    trie.insert(word)

print(trie.search('cart')) # True
print(trie.search('car')) # False
print(trie.search('calling')) # False
```

<br>

<br>

<br>

### REFERENCE

- [트라이, 컴퓨팅](https://ko.wikipedia.org/wiki/%ED%8A%B8%EB%9D%BC%EC%9D%B4_(%EC%BB%B4%ED%93%A8%ED%8C%85))
- [트라이 알고리즘 개념 및 파이썬 구현하기](https://velog.io/@gojaegaebal/210126-%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%8050%EC%9D%BC%EC%B0%A8-%ED%8A%B8%EB%9D%BC%EC%9D%B4Trie-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B0%9C%EB%85%90-%EB%B0%8F-%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%97%90%EC%84%9C-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0feat.-Class)
- [[Python/파이썬] Trie 알고리즘](https://m.blog.naver.com/cjsencks/221740232900)
- [트라이(Trie)](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Trie.md)