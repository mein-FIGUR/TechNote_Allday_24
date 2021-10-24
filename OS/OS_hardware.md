# 메모리

### 데이터를 저장하는 장치(기억장치)

* 프로그램(os,사용자 sw 등), 사용자 데이터 등
* 고성능일 수록 속도가 빠르지만 비용이 비싸다는 단점으로 인해 용량이 작아진다
* 레지스터, 캐시, 메인메모리는 프로세서가 프로그램과 데이터에 직접 접근할 수 있으며, 보조 기억장치는 프로그램과 데이터를 메인메모리에 옮겨야 실행 가능하다

### 메모리의 종류

##### 레지스터 

* 사용자 가시 레지스터
  * 데이터 레지스터 - 함수 연산에 필요한 데이터를 저장.

  * 주소 레지스터 - 주소나 주소를 계산하는데 필요한 주소의 일부분을 저장

* 사용자 불가시 레지스터
  * 프로그램 카운터 - 다음에 실행할 명령어의 주소를 보관하는 레지스터
  * 명령어 레지스터 - 현재 실행하는 명령어를 보관하는 레지스터
  * 누산기 - 데이터를 일시적으로 저장하는 레지스터
  * 메모리 주소 레지스터 - 프로세스가 참조하려는 데이터의 주소를 명시하여 메모리에 접근하는 버퍼 레지스터
  * 메모리 버퍼 레지스터 - 프로세서가 메모리에서 읽거나 메모리에 저장할 데이터 자체를 보관하는 버퍼 레지스터

##### 주 기억 장치

* 프로세서가 수행할 프로그램과 데이터를 저장
* DRAM을 주로 사용하며 프로세서에 직접 접근하는 메로리중 용량이 크고, 가격이 저렴하다
* 디스크 입출력 병목현상(I/O bottleneck)을 해소해준다

* 과거엔 디스크 속도에 비해 CPU속도가 느려서 큰 문제가 없었지만 CPU속도가 빨라짐에 따라 디스크 입출력 병목현상이 발생
* 그 현상을 해결하기위해 비용이 상대적으로 저렴하고 용량이크고 DISK보다는 빠른 메인메모리를 사용함으로서 CPU동작중 디스크에서 데이터를 받아서 미리 보내주는 주 기억장치를 사용

##### 캐시(Cache)

* 프로세서 내부에 있는 메모리

* 속도가 빠르고 가격이 비싸다
* 메인 메모리의 용도와 같이 입출력 병목현상 해소를 위해 사용
* DISK병목현상을 해소하기위해 메인메모리를 사용하듯이 메인메모리의 병목현상을 해소하기위해 캐시를 사용
* L1,L2,L3캐시등 여러 단계로 이루어져있다. L1이 가장작고 단계가 많아질수록 커지고 접근속도가 느려진다

##### 보조기억장치

* 프로그램과 데이터를 저장
* 프로세서가 직접 접근할 수 없기 때문에 메인메모리를 거쳐서 접근한다.
* 메인메모리보다 프로그램의 데이터가 더 크다면, 보조기억장치를 메인메모리처럼 사용한다(가상메모리)
* 용량이 크고, 가격이 저렴하다
* HDD, USB, CD 등이 있다.



##### 시스템 버스(System Bus)

* 하드웨어들이 데이터 및 신호를 주고받는 물리적인 통로
* 데이터 버스는 프로세서와 메인메모리, 주변장치 사이에서 데이터를 전송, 이를 구성하는 배선 수는 프로세서가 한번에 전송할 수 있는 비트 수를 결정하며, 이를 워드라고함
* 주소버스는 프로세서가 시스템의 구성요소를 식별하는 주소 정보를 전송, 배선수는 메인 메모리의 최대용량을 결정
* 제어 버스는 프로세서가 시스템의 구성요소를 제어하는데 사용. 연산장치의 연산종류와 메인메모리의 읽기 쓰기동작을 결정



* 레지스터의 동작과 시스템 버스

  1. PC -> 메모리주소 레지스터 -   PC에 저장된 주소를 프로세서 내부 버스를 통해 MAR에 전달

  2. MAR->메모리 버퍼레지스터 - MAR에 저장된 주소에 해당되는 메모리 위치에서 명령어 인출 후 MBR에 저장 제어장치는 메모리에 저장된 내용을 읽도록 제어신호 발생

     이 과정에서 MAR-> MBR에서 주소버스, 제어장치에서 메모리 제어를 하며 제어버스, 데이터 버스, 를 사용한다.

  3. 프로그램 카운터 +1 -> PC - 다음 명령어를 인출하기 위해 PC 증가

  4. MBR -> 명령어 레지스터 -> MBR에 저장된 내용을 IR에 전달



# 주변 장치

* 프로세서와 메모리를 제외한 하드웨어들
* 입력, 출력, 저장장치가 있다.
* 운영체제는 메모리, 프로세서 등을 관리하는 것 뿐만이 아닌 장치 드라이버, 인터럽트 처리, 파일 및 디스크 관리등도 한다.