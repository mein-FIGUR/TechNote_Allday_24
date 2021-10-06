# Load Balancing

- Load Balancing❓, Load Balancer❓
- Scale-up & Scale-out🔍
- Load Balancing의 종류🔍
- Load Balancer 주요 기능✔
- Load Balancer 동작 방식🔍
- Load Balancing Algorithm🔍
- Load Balancer 오류 대비⚠

<br>

<br>

## Load Balancing❓, Load Balancer❓

> 로드밸런싱(load balancing, 또는 부하 분산)은 컴퓨터 네트워크 기술의 일종으로, 둘 혹은 셋 이상의 중앙처리장치 혹은 저장치와 같은 컴퓨터 자원들에게 작업을 나누는 것을 의미한다.
>
> 쏟아지는 트래픽을 여러 대의 서버로 분산해주는 기술이 없다면, 한 곳의 서버에 모든 트래픽이 몰리는 상황이 발생한다. 아무리 성능이 뛰어난 서버도 모든 트래픽을 감당할 수 없기에, 여러 대의 서버를 구축하여 수많은 트래픽을 효과적으로 다뤄야 할 필요성이 있다. 이 때 필요한 기술이 로드 밸런싱이다.
>
> 로드밸런서는 **서버에 가해지는 부하를 분산해주는 장치 또는 기술**을 말한다. 

![img](https://post-phinf.pstatic.net/MjAxOTEyMTBfMjE3/MDAxNTc1OTU0ODk1ODQ3.-GJxkoK7Apn4l0K5L1OXN4NFGsseRoaNhW2r0KIQJdog.0BchcWEI-WS-uEb3iRRrD0JyO_6eZoIWh7xf4f4J2fMg.JPEG/%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%84%9C_%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98.jpg?type=w1200)

- 클라이언트와 서버풀(분산 네트워크를 구성하는 서버들의 그룹) 사이에 위치
- 한 대의 서버로 부하가 집중되지 않도록 트래픽을 관리해 각각의 서버가 최적의 퍼포먼스를 보일 수 있도록 함

<br>

<br>

## Scale-up & Scale-out 🔍

> 사업의 규모가 확장되고, 클라이언트의 수가 늘어나면 기존 서버로 증가된 트래픽에 대처할 수 없다. 이 때, 대처할 수 있는 방법은 크게 2가지가 있는데, 그것이 바로 **Scale-up**, **Scale-out** 이다.

![img](https://post-phinf.pstatic.net/MjAxOTEyMTBfMjk1/MDAxNTc1OTU1MDI2NTY4.Zxj8nWGb6G6jtHDAZPPDf-dPZnpb_hsd7ydWw5lW7vAg.AucOXPJnmLyGiHr8KpVD9Dsy59FsWv5p7qJnSyW_YFAg.JPEG/%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1_%EC%8A%A4%EC%BC%80%EC%9D%BC.jpg?type=w1200)

- Scale-up
  - 서버가 더 빠르게 동작하기 위해 하드웨어 성능을 올리는 방식
  - 서버 자체의 성능을 확장
- Scale-out
  - 기존 서버와 동일하거나 낮은 성능의 서버를 두 대 이상 증설하여 운영
  - 로드밸런싱이 반드시 필요

<br>

<br>

## Load Balancing의 종류🔍

- OSI 7계층에 따라 나뉨
  - L2(Data Link): MAC 주소 기반 로드 밸런싱
  - L3(Network): IP주소 기반 로드 밸런싱
  - L4(Transport): 포트 번호 기반 로드 밸런싱
  - L7(Application): URL, HTTP 헤더, 쿠키 등 사용자의 요청을 기준으로 로드 밸런싱 

<br>

### L4 Load Balancer

- TCP/UDP 포트 정보를 바탕으로 함
- 데이터를 들여다보지 않고 패킷 레벨에서 로드를 분산하기 때문에 속도가 빠르고 효율이 높음
- 데이터의 내용을 복호화할 필요가 없어 안전함
- 패킷의 내용을 볼 수 없어 섬세한 라우팅 불가능
- 사용자의 IP가 수시로 바뀌는 경우라면 연속적인 서비스를 제공하기 어려움

![img](https://post-phinf.pstatic.net/MjAxOTEyMTBfNCAg/MDAxNTc1OTU1MzY3OTM2.nG91HOEOh6Sc1AuUgbN3O4pcnEI-rh24UKSrrrjkrcsg.VcG18MidW4az7Oh0RQfRPLDBHNRyGayE1BsQxDImL3Ig.JPEG/L4-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1.jpg?type=w1200)

<br>

### L7 Load Balancer

- TCP/UDP 정보는 물론 HTTP의 URL, FTP의 파일명, 쿠키 정보 등을 바탕으로 함
- 상위 계층에서 로드를 분산하므로 섬세한 라우팅 가능
- 캐싱 기능 제공
- 비정상적인 트래픽 사전에 필터링할 수 있어 서비스 안정성이 높음
- 클라이언트가 로드밸런서와 인증서를 공유하기 때문에 공격자가 로드밸런서를 통해 클라이언트의 데이터에 접근할 수 있는 보안 상의 위험성 존재

![img](https://post-phinf.pstatic.net/MjAxOTEyMTBfMjA1/MDAxNTc1OTU1MzgxODY5.odnG4CRES0e5bH7sOKyWRP1c8uO_XC4VX9A3HPeI1JQg.lNL2eJYbMz6NX1e5YFzfHDMQHn4YrdOJR2VYHmq5e1Ig.JPEG/L7-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1.jpg?type=w1200)

<br>

<br>

## Load Balancer 주요 기능✔

- NAT(Network Address Translation)
  - IP주소를 변환해주는 기능
  - Private IP를 Public IP로 변경(반대도 가능)
- Tunneling
  - 데이터를 캡슐화해서 연결된 상호 간에만 캡슐화된 패킷을 구별하여 해제 가능
- DSR(Direct Server Routing)
  - 서버에서 클라이언트로 되돌아가는 경우(요청에 대한 응답), 목적지를 클라이언트로 설정한 다음 네트워크 장비나 로드밸런서를 거치지 않고 바로 클라이언트로 찾아감
  - 로드밸런서의 부하를 줄여줌

<br>

<br>

## Load Balancer 동작 방식🔍

- Bridge/Transparent Mode
  1. 유저가 로드 밸런서로 요청 전송
  2. 로드 밸런서는 NAT 적용하여 IP/MAC 주소 변조, 실제 서버로 트래픽 요청
  3. 서버가 받은 요청에 대한 응답 전송
  4. 로드 밸런서는 NAT 적용하여 출발지 IP주소를 로드밸런서의 가상 IP주소로 변조하여 유저에게 전달
- Router Mode
- One Arm Mode
- DSR Mode

<br>

<br>

## Load Balancing Algorithm🔍

- 라운드 로빈(Round Robin)
  - 서버에 들어온 요청을 순서대로 돌아가며 배정하는 방식
  - 여러 대의 서버가 동일한 스펙을 갖고 있고, 서버와의 연결이 오래 지속되지 않는 경우 적합
- 가중 라운드 로빈(Weighted Round Robin)
  - 각각의 서버마다 가중치를 매기고 가중치가 높은 서버에 요청을 우선적으로 배분
  - 서버들의 트래픽 처리 능력이 다른 경우 사용되는 방식
- IP 해시(IP Hash, Source Hash Scheduling)
  - 클라이언트의 IP주소를 특정 서버로 매핑하여 요청 
  - 사용자가 항상 동일한 서버로 연결되는 것을 보장
- 최소 연결(Least Connection)
  - 요청이 들어온 시점에 가장 적은 연결상태를 보이는 서버에 우선적으로 배분
  - 세션이 길어지거나, 분배된 트래픽이 일정하지 않은 경우에 적합
- 최소 리스폰 타임(Least Response Time)
  - 서버의 현재 연결 상태와 응답 시간을 고려하여 트래픽 배분
  - 가장 적은 연결 상태와 가장 짧은 응답시간을 보이는 서버에 우선적으로 로드를 배분

<br>

<br>

## Load Balancer 오류 대비⚠

- Load Balancer를 이중화하여 장애를 대비

![No Image](https://nesoy.github.io/assets/posts/20180602/8.gif)

- 이중화된 Load Balancer들은 서로 Health Check를 함
- Primary Load Balancer가 동작하지 않으면, 여분의 Load Balancer로 변경 후 운영

<br>

<br>

### REFERENCE

- [부하분산-위키백과](https://ko.wikipedia.org/wiki/%EB%B6%80%ED%95%98%EB%B6%84%EC%82%B0)
- [로드밸런서(Load Balancer)의 개념과 특징](https://m.post.naver.com/viewer/postView.nhn?volumeNo=27046347&memberNo=2521903)
- [로드 밸런서(Load Balancer)란?](https://nesoy.github.io/articles/2018-06/Load-Balancer)
- [로드밸런서란?(L4, L7)](https://vaert.tistory.com/189)
- [로드밸런서의 종류와 동작방식](https://deveric.tistory.com/91)
- [네트워크의 부하분산, 로드밸런싱(Load Balancing) 그리고 로드밸런서(Load Balancer)](https://stevenjlee.net/2020/06/30/%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC%EC%9D%98-%EB%B6%80%ED%95%98%EB%B6%84%EC%82%B0-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1-load-balancing-%EA%B7%B8/)

