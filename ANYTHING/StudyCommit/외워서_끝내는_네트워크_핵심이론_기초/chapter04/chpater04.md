#4장 - L3 수준에서 외울 것들
---
- ipv4 주소의 기본구조
  - 32bit 주소체계
  - 8bit.8bit.8bit.8bit 로 구성되어있다.
  - 앞에 24bit -> Network ID
    - 택배로 치면 큰 섹터(동 이든, 구 이든) 를 구분하는
  - 뒷 8bit -> Host ID
    - 택배로 치면 번지 정도.

---
- L3 Ip Packet 으로 외워라
  - Packet 이라는 말은 L3 IP Packet 으로 외우자.
  - Header 와 Payload 로 나뉘며 이는 상대적인 분류이다.
  - 최대 크기는 MTU
    - 특별한 이유가 없다면 1500 bytes (1.4kb)
  - header
    - Src(출발지) -> Dst(목적지)

---
- Encapsulation 과 Decapsulation
  - Encapsulation
    - 단위화 했다.(포장)
  - Decapsulation
![img.png](img.png)


---
- 패킷의 생성과 전달
  - Process -> segment -> packet -> frame -> L2 Access Switch -> Router -> internet

---
- Socket
  - 엔드포인트, 
  - 파일을 추상화한, 커널모드 프로토콜을 추상화한 유저모드 어플리케이션이 접근할 수 있도록 추상화한 인터페이스이다.
  - 응용프로그램에서 tcp/ip를 이용하는 입구 역할을 하며, 응용프로그램과 소켓 사이의 인터페이스 역할을 하고있다.
- 계층형 데이터 단위
  - 
![img_1.png](img_1.png)
  - Segment - Segmentation
  - 가래 떡집 생각하면 될듯.

---
- TCP/IP 송수신 구조
![img_2.png](img_2.png)

---
- IP 헤더 형식
  - ![img_3.png](img_3.png)

---
- 서브넷 마스크와 CIDR
  - 과거?의 Subnet Mask 의 용도
    - IP 에  A, B, C 라는 클래스 개념(IPV4 를 자르는 방식에 따라 등급이 달랐다.)을 도입하여 등급을 매겼다.
    - 이러한 등급을 잘리내려는 방법론으로 서브넷 마스크가 사용됐다.]
    - 그당시에는 효율적이였으나, 근래에는 아이주소에 클래스라는 개념을 사용하지않는다.
      - ![img_4.png](img_4.png)
    - 근래에 들어서는 표기법을 다르게 사용한다.(CIDR(싸이더))
      - ![img_5.png](img_5.png)


  