#ip dns ddns..

- DNS(Domain Name Systme)
  - www.naver.com -> naver.com 부분을 도메인 이라 한다.
  - www -> host 네임이라 한다.
  - ROOT DNS 서버 - 13곳으로 .com, .net .org ... 에 관한 도메인을 담당하는 ip주소를 반납한다.
  - .com 담당 서버는 naver.com 을 가지고있는 DNS 서버의 IP 주소를 반환
  - naver.com 담당 서버는 여러 호스트네임별 IP주소들이 있다(ex: www.naver.com, mail.naver.com, blog.naver.com....)
  - www.naver.com 의 ip 주소를 얻어낸뒤, 브라우저에 반환한뒤 브라우저 접속이 이루어진다.

- DNS 스푸핑(spoofing)
  - 요청 DNS 정보를 가로채어 악성 사이트로 접속하게끔 정보를 반환한다.

- DNS 구매
  - 국내: 후이즈, 가비아 등.. 해외: GoDaddy 등

- DDNS 
  - 동적 DNS 유동 IP 를 감지해서 고정된 도메인에 연결시켜준다.


- IPv4 형식
  - 3개의 숫자(0~255) 4개의 그룹이 점으로(.)이어져있다.
  - 처음 대중화된 규약 - 256 의 4승에 달하는 IP 주소를 가질 수 있는 형식
    - 4,294,967,296 대략 43억개의 ip가 나올 수 있다.
- 공인 IP
  - 절대 유일한 주소 ex) 서울시 강남구 강남대로 12 센트럴자이
- 사설 IP
  - 공인 IP 안에서만 유일한 부분 ex)101동 101호