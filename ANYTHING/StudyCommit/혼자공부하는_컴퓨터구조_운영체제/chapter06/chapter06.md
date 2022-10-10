#6장 - 메모리와 캐시 메모리

---
#6-1 RAM 의 특성과 종류
- RAM 
- 명령어와 데이터 저장, 휘발성 저장 장치(volatile memory)
- RAM 이 크면 많은 프로그램을 동시에 실행하는 데에 유리하다.
- RAM 의 종류
  - DRAM (Dynamic RAM)
    - 저장된 데이터가 동적으로 변하는(사라지는) RAM 을 의미한다. 즉 DRAM 은 시간이 지나면 저장된 데이터가 점차 사라지는 RAM
    - 그렇기에 DRAM 은 데이터의 소멸을 막기 위해 일정 주기로 데이터를 재활성화 해야 한다.
    - 우리가 일반적으로 사용하는 사용하는 메모리이다.
      - 소비전력이 비교적 낮고, 저렴하고, 집적도(더 작고 뺵뺵하게 만들 수 있다)가 높기 때문에 대용량으로 설계하기가 용이하기 때문.
  - SRAM (Static RAM)
    - 저장된 데이터가 변하기 않는 RAM 을 의미한다.
    - SRAM 은 DRAM 보다 일반적으로 속도가 더 빠르다.
    - DRAM 보다 소비전력이 크며, 집적도가 낮고, 가격도 더 비싸다.
    - 대용량으로 만들어질 필요는 없지만 속도가 빨라야 하는 저장 장치 즉 "캐시 메모리"에서 사용된다.
  - SDRAM (Synchronous Dynamic RAM)
    - SRAM 과 DRAM 의 합성어 같지만 **합성어가 아니다**
    - SDRAM 은 클럭 신호와 동기화된, 발전된 형태의 DRAM 이다.
    - 클럭 신호와 동기화 되었다라는 것은, 클럭 타이밍에 맞춰 CPI 와 정보를 주고받을 수 있다는 것을 의미한다.
  - DDR SDRAM (Double Data Rate SDRAM)
    - 최근 가장 흔히 사용되는 RAM
    - 대역폭을 넓혀 속도를 빠르게 만든 SDRAM 이다.
    - *한클럭당 하나씩 데이터를 주고받을 수 있는 SDRAM 을 SDR SDRAM(Single Data Rate SDRAM) 이라 부르기도 한다.
    - DDR SDRAM 대역폭 ex) 2차선
    - DDR2 SDRAM 은 DDR SDRAM 보다 대역폭이 두배 넓은..(4차선..)
    - DDR3 SDRAM 은 DDR2 SDRAM 보다 대역폭이 두배 넓은..(8차선..)
    - DDR4 SDRAM 은 DDR3 SDRAM 보다 대역폭이 두배 넓은..(16차선..)
    16차선
---

