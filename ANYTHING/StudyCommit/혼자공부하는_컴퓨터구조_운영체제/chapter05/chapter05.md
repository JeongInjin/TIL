#5장

#5-1 빠른 CPU 를 위한 설계 기법

- 컴퓨터 부품은 클럭 신호에 맞춰 움직인다.
- CPU 는 명령어 사이클 이라는 정해진 흐름에 맞춰 명령어들을 실행한다.


- 클럭
  - 클럭 속도는 헤르츠(Hz) 단위로 측정 -> 1초에 클럭이 몇 번 반복되는지를 나타냄
    - 2.5GHz -> 1초에 클럭이 25억번 반복
  - 클럭속도는 일정하지않다. 기본속도(base) 와 최대 클럭 속도(Max) 가 유연하게 작동한다


- 코어
  - CPU: 명령어를 실행하는 부품
  - **'명령어를 실행하는 부품'**은 오늘날 **코어** 라는 용어로 사용됨.
  - CPU 는 단순히 명령어를 실행하는 부품에서 -> 명령어를 싱행하는 부품을 여러 개 포함하는 부품 으로 명칭의 범위가 확장됨
  - ex)8코어 -> 명령어를 실행하는 부품을 여덟 개 포함하고 있다.
- 멀티코어
  - 코어를 여러 개 포함하고 있는 CPU 를 **멀티코어 CPU** 또는 **멀티코어 프로세서** 라고 부른다.


- 스레드
  - 실행 흐름의 단위
- 하드웨어적 스레드
  - CPU 에서 사용되는..
  - 하드웨어적으로 정의: 하나의 코어가 동시에 처리하는 명령어 단위
  - 하나의 코어에서 여러 명령어를 동시에 처리하는 CPU 를 멀티스레드 프로세서 또는 멀티스레드 CPU 라고 한다.
  - 하이퍼스레딩? -> 인텔의 멀티스레드 기술에 파이퍼스레딩이라는 명칭을 부여함.
  - 논리 프로레서 라고 부리기도 함

- 소프트웨어적 스레드(스레드)
  - 프로그램에서 사용되는..
  - 하나의 프로그램에서 독립적으로 실행되는 단위

---
#5-2 명령어 병렬 처리 기법

- 명령어 파이프라이닝
  - 명령어 처리 과정을 클럭 단위로 나뉘어보면 일반적으로 다음과 같이 나눌 수 있다.
    1. 명령어 인출(Instruction Fetch)
    2. 명령어 해석(Instruction Decode)
    3. 명령어 실행(Execute Instruction)
    4. 결과 저장(Write Back)
  - CPU 는 각 단계가 겹치지 않는다면**각 단계를 동시에 실행할 수 있다.**
  - 공장 생산 라인과 같이 명령어들을 "명령어 파이프라인"에 놓고 동시에 처리하는 기법을 "명령어 파이프라이닝" 이라 한다.
  - 파이프라이닝이 높은 성능을 가져오는 하지만, 특정 상황에서는 성능 향상에 실패하는 경우도 있다.
  - 이러한 상황을 **파이프라인 위험(pipeline hazard)** 라고 부른다.
  - 파이프라인 위험
    - 데이터 위험(data hazard)
      - 데이터 의존적인 두 명령어를 무작정 동시에 실행하려고 하면 파이프라인이 제대로 작동하지 않음
      - ex) 명령어 1 의 결과값을 명령어 2에서 실행하려할때.
    - 제어 위험
      - 프로그램 실행 흐름이 봐뀌어 프로그램 카운터 값에 갑작스러운 변화가 생겨 파이프라인에 미리 가지고 와서 처리 중이였던 명령어들이 아무 쓸모가 없어짐
      - 참고: 이를 위해 사용하는 기술 중 하나가 "분기 예측(branch prediction)"이다.
        - 프로그램이 어디로 분기할지 미리 예측한 후 그 주소를 인축하는 기술
    - 구조적 위험
      - 명령어들을 겹처 실행하는 과정에서 서로 다른 명령어가 동시에 ALU, 레지스터 등과 같은 CPU 부품을 사용하려고 할때 발생
      - 구조적 위험은 "자원 위험(resource hazard)" 이라고도 부른다
- 슈퍼스칼라
  - 오늘날 대부분 CPU 에서는 여러개의 파이프라인을 이용한다.
  - CPU 내부에 여러 개의 명령어 파이프라인을 포함한 구조를 "슈퍼스칼라" 라고 한다.
  - 슈퍼스칼라 구조로 명령어 처리가 가능한 CPU 를 "슈퍼스칼라 프로세서", "슈퍼스칼라 CPU" 라고 한다.
  - 슈퍼스칼라 프로세서는 이론적으로는 개수에 비례하여 프로그램 처리 속도가 빨라지지만, 
    - 파이프라인 위험 등의 예상치 못한 문제가 있어 실제로는 반드시 파이프라인 개수이 비례하여 빨라지지는 않는다.
- 비순차적 명령어 처리
  - 명령어들을 순차적으로 실행하지 않는 기법(합법적인 새치기)
  - 서로 데이터 의존성이 없고, 순서를 봐꿔 처리해도 수행 결과에 영향을 미치치 않는 명령어들을 먼저 실행하여 파이프라인이 멈추는것을 방지하는 기법이다.

---
#5-3 CISC 와 RISC

- ISA
  - CPU 가 이해할 수 있는 명령어들의 모음을 명령어 집합 구조(ISA:Instruction Set Architecture) 라고 한다. CPU 마다 ISA 가 다를 수 있다.
  - **ISA 눈 CPU 의 언어이자, 하드웨어가 소프트웨어를 어떻게 이해할지에 대한 약속이다.**
- CISC
  - CISC: Complex Instruction Set Computer - 복잡한 명령어 집합을 활용하는 컴퓨터(CPU)
  - CISC 는 복잡하고 다양한 수의 가변 길이 명령어 집합을 활용한다.
  - 과거 메모리를 최대한 아끼며 개발해야 했던 시절에 인기가 높았다
  - 치명적인 단점으로는 활용하는 명령어가 복잡하고, 다양한 기능을 제공하는 탓에 명령어의 크기와 실행되기까지의 시간이 일정하지 않는다.
  - **즉 파이프라인을 구현하는 것이 어렵다.**
- RISC
  - RISC: Reduced Instruction Set Computer - 축소된 명령어 집합을 활용하는 컴퓨터(CPU) 
  - CISC 에 비해 명령어의 종류가 적다.
  - 짧고 규격화된 명령어, 되도록 1클럭 내외로 실행되는 명령어를 지향한다.
  - **고정 길이 명령어를 활용**

- 정리
  - ISA 는 CPU 의 언어이자, 하드웨어가 소프트웨어를 어떻게 이해할지에 대한 약속.
  - CISC 는 복잡하고 다양한 종류의 가변 길이 명령어 집합을 활용한다.
  - RISC 는 단순하고 적은 종류의 고정 길이 명령어 집합을 활용합니다.

---





