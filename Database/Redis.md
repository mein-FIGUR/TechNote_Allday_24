# Redis

<br>

- Redis❓
- Redis 사용 용도🔍
- Redis 특징🔍
- 주의사항⚠

<br>

## Redis❓

>Redis는 Remote dictionary server의 약자로써,  `키-값`구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터베이스 관리 시스템(`DBMS`)이다. 모든 데이터를 메모리에 저장하고 조회하기에 빠른 Read, Write 속도를 보장하는 비 관계형 데이터베이스이다. 

- 크게 5가지 형식을 지원한다.
  - `String`, `Set`, `Sorted Set`, `Hash`, `List`
- I/O가 빈번히 발생해 다른 저장 방식을 사용하면 효율이 떨어지는 경우에 사용

<br>

## Redis 사용 용도🔍

- Message Queue
- Shared Memory
- Remote Dictionary
  - RDBMS의 캐시 솔루션으로 사용 용도가 높음
  - Disk에서 데이터를 꺼내오는 것이 Memory에서 읽어들이는 것보다 천 배 가량 더 느림

<br>

## Redis 특징🔍

- 영속성(Persistance)을 지원하는 인메모리 데이터 저장소
  - Redis는 데이터를 disk에 저장할 수 있음
  - 저장하는 방식으로 `snapshot`, `AOF` 방식 활용
  - Redis 공식문서의 권장사항은 두 방식을 혼용해서 사용하는 것
    - 주기적으로 snapshot으로 백업하고, 다음 snapshot까지의 저장을 AOF방식으로 수행

> snapshot: 특정 시점의 데이터를 disk에 옮겨담는 방식으로, Blocking 방식의 SAVE와 Non-blocking 방식의 BGSAVE가 있음
>
> AOF: Redis의 모든 write/update 연산 자체를 모두 log 파일에 기록하는 형태, 서버가 재시작할 시 write/update를 순차적으로 재실행, 데이터를 복구

- 읽기 성능 증대를 위한 서버 측 복제를 지원
- 쓰기 성능 증대를 위한 클라이언트 측 샤딩(Sharding)을 지원
- 다양한 데이터 타입
- C언어로 작성되어 가비지 컬렉션 동작에 따른 성능 문제 등에서 자유로움

<br>

## 주의사항⚠

- 서버에 장애가 생기는 경우, 데이터 유실이 발생하므로, snapshot과 AOF기능을 통한 복구 시나리오를 제대로 세워야 함
- 잘못된 데이터가 캐싱되지 않아야 함
  - 레디스와 캐싱하고자 하는 데이터 저장소의 데이터가 서로 일치하는지 주기적인 모니터링과 솔루션 필요
- 생성한 키를 선택적으로 삭제하기 어려움
  - 일괄 삭제, 일정 시간 이후 삭제, 기간 만료 후 삭제 등 3가지 방법을 활용해 키를 삭제할 수 있음

<br>

<br>

### REFERENCE

- [레디스(Redis)는 언제 어떻게 사용하는 게 좋을까](https://brunch.co.kr/@skykamja24/575)
- [[Redis, 레디스] 레디스 소개 및 아키텍처, 주의할 점(Redis Overview, Redis Architecture, Tool Tip)](https://engkimbs.tistory.com/869)
- [레디스(Redis)란 무엇인가?](https://jyejye9201.medium.com/%EB%A0%88%EB%94%94%EC%8A%A4-redis-%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-2b7af75fa818)
- [레디스](https://ko.wikipedia.org/wiki/%EB%A0%88%EB%94%94%EC%8A%A4)
