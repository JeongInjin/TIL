#커널 오브젝트

컴퓨터 과학에서 커널(kernel)은 컴퓨터 운영 체제의 핵심이 되는 컴퓨터 프로그램으로, 시스템의 모든 것을 완전히 통제한다.[1] 운영 체제의 다른 부분 및 응용 프로그램 수행에 필요한 여러 가지 서비스를 제공한다. 핵심(核心)[2]이라고도 한다.
- https://ko.wikipedia.org/wiki/%EC%BB%A4%EB%84%90_(%EC%BB%B4%ED%93%A8%ED%8C%85)
- 커널에 의해 관리되는 리소스 정보를 담고 있는 데이터 블록(https://www.youtube.com/watch?v=tYs6q_Lsi_0)
- 운영체제에 의해 관리되는 리소스 들을 관리하기위해 데이터를 내부적으로 저장해 두는데 이것을 커널 오브젝트라 한다

- https://www.redhat.com/ko/topics/linux/what-is-the-linux-kernel
  - 커널의 기능(다음과 같은 4가지 기능을 수행합니다.)
    - 메모리 관리: 메모리가 어디서 무엇을 저장하는 데 얼마나 사용되는지를 추적합니다.
    - 프로세스 관리: 어느 프로세스가 중앙 처리 장치를 얼마나 오랫동안 사용할지를 결정합니다.
    - 장치드라이버: 하드웨어와 프로세스 사이에서 중재자/인터프리터 역할을 수행합니다.
    - 시스템 호출 및 보안: 프로세스의 서비스 요청을 수신합니다.
  - 