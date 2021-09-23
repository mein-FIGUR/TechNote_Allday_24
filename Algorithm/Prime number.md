# 👀Prime number(소수 구하기)

## 1. 에라토스테네스의 체

---

- 소수(Prime number) 구하는 알고리즘
- 고대 그리스 수학자 에라토스 테네스가 발견

![에라토스테네스의 체](https://upload.wikimedia.org/wikipedia/commons/b/b9/Sieve_of_Eratosthenes_animation.gif)

- 2부터 소수를 구하고 싶은 구간의 모든 수를 나열 한다. 그림에서 회색사각형 수들이 해당
- 2는 소수이기에 오른쪽에 2를 쓴다.(빨간색)
- 자기 자신을 제외한 2의 배수를 모두 지운다.
- 남아있는 회색 수 가운데 3은 소수이기에 오른쪼에 3을 쓴다. (초록색)
- 자기 자신을 제외한 3의 배수를 모두 지운다.
- 같은 방식으로 5(파란색), 7(노란색) 등 반복하며 진행한다.
- 그림의 경우 11² > 120 이므로 11보다 작은 수의 배수들만 지워도 충분, 즉 120보다 작거나 같은 수 가운데 2, 3, 5, 7의 배수를 지우고 남는 수는 모두 소수이다.

### ✅ 파이썬으로 구현

```python
def prime_list(n):
    # 에라토스테네스의 체 초기화: n개 요소에 True 설정(소수로 간주)
    sieve = [True] * n

    # n의 최대 약수가 sqrt(n) 이하이므로 i=sqrt(n)까지 검사
    m = int(n ** 0.5)
    for i in range(2, m + 1):
        if sieve[i] == True:           # i가 소수인 경우
            for j in range(i+i, n, i): # i이후 i의 배수들을 False 판정
                sieve[j] = False

    # 소수 목록 산출
    return [i for i in range(2, n) if sieve[i] == True]
```

### ✅ 관련문제

- 백준 1929번 소수 구하기

- https://www.acmicpc.net/problem/1929

- ```python
  # 에라토스테네스의 체 활용
  def eratos(x, y):
  	sieve = [True] * (y+1) # 에라토스 테네스체 초기화
  	sieve[1] = False # 1이 해당하지 않도록 제외
  	m = int(y ** 0.5) #제곱근 까지구하도록
  	for i in range(2, m+1):
  		for j in range(i+i, y+1, i):
  			sieve[j] = False
  	return [i for i in range(x, y+1) if sieve[i] == True] # x 이상 y이하에서 소수 구하기
  
  
  x, y = map(int, input().split())
  result = eratos(x, y)
  
  for i in result:
  	print(i)
  ```

---

## 2. 추가적인 내용

- 일반적인 소수판별 방법은 자연수 N을 2 부터 N-1까지의 수로 나누어 나머지가 0인 경우(나누어 떨어지는 경우)가 없다면 소수라고 판별 할 수 있다. 
- 하지만 시간복잡도에서  N까지 확인해야함으로 O(N)의 시간복잡도를 가진다. (따라서 시간초과가 뜨는 경우가 많다.... ㅠㅠ )
-  따라서 __N의 제곱근__ 까지 확인 하는 방법을 통해 소수 판별을 한다면 시간 복잡도를 줄일 수 있다. 





# 참고자료

1. 에라토스테네스의 체 - 위키백과 (https://ko.wikipedia.org/wiki/%EC%97%90%EB%9D%BC%ED%86%A0%EC%8A%A4%ED%85%8C%EB%84%A4%EC%8A%A4%EC%9D%98_%EC%B2%B4)