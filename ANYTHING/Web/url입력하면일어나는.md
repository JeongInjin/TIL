#google.com 을 입력하면

윈도우
www.google.com enter ->
1.자신의 pc 메모리를 찾아 DNS Cache 를 찾는다  
2.없을경우 hosts File 을 찾는다  
3.없을경우 DNS 에 호출한다  
3.1.대부분 공유기를 쓰는데, 이 공유기가 DNS 포워딩을 해주기도한다.  
3.2.공유기가 응답이 없을경우 kt,sk 등 인터넷 서비스 프로바이더(ISP)가 응답한다.(DNS Cache 한다)  
4.ISP 조차 DNS 정보가없을경우 Root DNS 에게 질의한다.   
4.1 com 을 다루는 DNS 목록을 날려준다(하나의 선택을 하게된다.)  
4.2 com 의 목록중에 naver 를 질의후 반환한다.  
4.3 naver 의 목록중에 www 를 묻는다 -> IP 주소를 반환한다.

이러한 응답에는 응답 + 유효기간이 뭍어있다.(캐싱하기 위함)

*루트 DNS 는 전세계에 13대가 있다.  

- GSLB 도 바드시 언급해 준다.(CDN- Content Delivery Network 도 같이)
  - 터미널을 열어 nslookup www.google.com
  - CDN:
    - 