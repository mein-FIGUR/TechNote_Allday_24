# [컴퓨터구조] 파이프라이닝 3 

## 1. 제어 해저드(Control Hazard)

- 분기(jump, branch 등) 명령어에 의해서 발생한다. 
- ![image-20211010210102504](C:\Users\super\AppData\Roaming\Typora\typora-user-images\image-20211010210102504.png)

### <제어 해저드 해결 방법>

- __분기 예측__ : 명령이 분기하는 지를 미리 예측하여, 명령을 변화시키는 방법으로 지연이 발생하지 않도록 하는 기술
- ![image-20211010210807263](C:\Users\super\AppData\Roaming\Typora\typora-user-images\image-20211010210807263.png)
- __브랜치 지연__ : 컴파일러가 분기문 발견 시, nop (No operation을 의미)혹은 분기와 관련 없는 명령을 추가 하도록 프로그램 순서를 재배치
- ![image-20211010210839427](C:\Users\super\AppData\Roaming\Typora\typora-user-images\image-20211010210839427.png)
- __프로그래밍 방식__ : 조건분기를 최소화하도록 프로그래밍하여 제어 해저드를 최소화 (Inline 메소드를 활용, Loop unrolling 사용)



### <분기예측이란?>

- ![image-20211010211607611](C:\Users\super\AppData\Roaming\Typora\typora-user-images\image-20211010211607611.png)
- 파이프라인을 통한 명령 실행 중 조건 분기 명령의 실행이 종료될 때까지 다음 명령을 대기하지 않고 분기를 예측 실행하여 파이프라인 처리 성능 저하를 최소화하는 CPU 실행 기술
- 다음 실행될 조건문이 어떤 곳으로 분기할 것인지를 확실히 알게 되기 전에 미리 추측하여 실행하여 파이프라인 효율성 확보

## <분기 예측이 왜 필요한가?>

- 다음 실행될 명령어의 분기방향과 분기 목적지 예측을 통해 명령어를 미리 실행하여 파이프라인 효율성을 확보
- 파이프라인 프로세서에서 제어 해저드로 인한 Stall 발생 시 분기예측은 항상 필요

## <분기 방향 예측>

![image-20211010212326578](C:\Users\super\AppData\Roaming\Typora\typora-user-images\image-20211010212326578.png)

## <분기 목적지 예측>

![image-20211010212422217](C:\Users\super\AppData\Roaming\Typora\typora-user-images\image-20211010212422217.png)



