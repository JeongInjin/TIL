# module 화 작업 - 2022.02.11

현재의 방식 구조는 모놀리틱 형식의 프로젝트 였지만 추후 프로젝트의 마이크로서비스 아키텍처 즉 MSA 로 가기위한 발판의 기틀을 만들어 놓기 위해 모듈화를 결정 하였습니다.  
기존의 프로젝트를 참고하여 만들었지만, DDD 의 기반 지식이 얉고 아직 부족한 아키텍처 설계로 인하여 숙제가 많이 남아 있는거 같습니다.


좋은 아키텍처 모델링을 한다는게 참 어려운것 같고, 이번을 계기로 좀더 확장된 서비스를 할때, 구조를 어떻게 가져가면 좋을지, 의존관계를 어떻게 맺어야 할지에 대한 고민을 하게되서 좋은 경험이였습니다.

배민에서 모듈화 방식의 아키텍처 구성을 어떻게 하고, 어떠한 고민을 하였는지에 대한 싸이트를 남기고, 추후 이해도가 높아지면 모듈화의 리펙터링을 진해하면 좋을 듯 싶습니다.

참고사이트 : https://techblog.woowahan.com/2637/

느낌점 : 좋은 설계와 개발자가 편한 아키텍처의 구성은 언제나 어려운것 같다.  msa 와 ddd 의 학습이 필요한 것 같다.

~~~
삽질 : 모듈을 만들고 구성하는건 쉬웠지만 이상하게만큼, gradle에서 root 프로젝트 안에 하위 모듈들이 제대로 구성이 안되는 이슈?가 있었다.

    root  
     |---core  
     |---community_api  
    core  
    community_api  
    
뭐 이런식으로 구성이 된다해야 할까..처음구성하는거라 이해도가 없이 마음이 급했는지 바보같이 여기서 시간을 지체하였습니다.  
그리고 인텔리제이 캐시 문제같아 보이는(같은루트에 같은폴더에 프로젝트를 계속 생성)이슈도 나온거 같아 제대로 된 설정을 하였지만..아닌 줄 알았던..  
작은 이슈도 있었습니다.  
결국 해결은 그냥 필요없는 구조의 모듈은 삭제처리 하는 방식으로 처리하였습니다.
~~~
TODO LIST :
1.모듈화를 더 이해하여 좀더 명확한 설계로 탈바꿈.  
1-1.모듈화를 세세하게 더 구성하는게 어떠한 장/단점이 있는지 파악해서 구조변경  
2.현재 root 프로젝트에 의존성이 한곳에 몰려있는데, 이러한 의존관계를 좀더 세밀하게 프로젝트별로 가져갈 수 있도록 구성  
3.스프링의 Bean 주입을 현재 mainClass 에 componentscan 형식의 basepakage 를 적어줘야하는데, 모듈이 많아질때 마다, 불편함이 있어, 공통화 시키기.  
ps.선수지식 : MAS, DDD 이지 않을까?

# 회사..일 - 2022.02.27

회사에서 요즘 신규 프로젝트를 진행하면서 최초 프로젝트 구성부터 설정까지 모든걸 경험해 보고있는 듯하다.  
주말동안은 스프링 시큐리티 쪽 구성을 진행하였고, 신규 프로젝트다 보니
기본 유틸이나 factory 성 코드들이 없어서 하나하나 집어넣고있다.  
언어도 자바가 아닌 코틀린 이다 보니 적응을 아직 하고는 있지만 어느정도 익숙한거 같다.  
이렇게 처음부터 끝가지 할 수 있는 기회는 흔치 않은것 같고, 현재 매우 좋은 기회라 생각한다.  
코더가 되지 않으려 노력하고있다. 최소한 소스를 이해하고 적용하려고 노력하고 있다..  
뜨끔 거리지만 시큐리티쪽은.. 반쯤 이해한거같다..솔직히 너무 어렵다..흑흑..

# 2022.03.03

다행히 시큐어 코딩이 내가원하는 방식으로 구성은 잘 된듯하다.  
조금 아쉬운 부분이 있다면 이해를 거의 완벽히 한 상태가 아니라는것..너무나 어려웠다.  
but 고생한만큼 잘 작동하는거 같아 나중에 좀 더 고도화를 한다면 좀 더 좋은 방식으러 개선할 여지가 있어보인다.  
일단 레디스 도입을 빨리 해야할듯하다..  
디비를 계속 호출한다는게 마음에 걸린다..  
또다른 서버와의 통신하여 정보를 가져오는 로직이 있다는거도 좀 그렇다..  
레디스를 이용해서 값을 갱신하는 방법 도입과 토큰을 좀 더 적극적으로 활용하는 방법을 찾아봐야할듯 하다.  
스터디를 진행하려고 생각중이다..  
항상 내 맘대로 되는건 없고..나만 하고 싶다고 되는것도 어니고..생각이 복잡하다..  
이놈의 일복은 어딜가나 너무 많은거 같다.  좋은건지 나쁜건지..  
내일도 화이팅 할것이다.

#2022.03.04

aop 형식의 로깅방식에서 -> interceptor 형식으로 변경 후 완성된줄 알았다.  
문제가 발생한 부분이..발견되었다..  
contentType 이 multiPart 형식으로 들어오면 ContentCachingResponseWrapper = response as ContentCachingResponseWrapper 부분이 exception 이 발생되었디.  
일단 webView 를 내가 돌릴 수 없는 상황이라 급하게 방어 코드를 넣었다.  
request is MultipartHttpServletRequest 인지 체크해서 해당 로직이 true 면 request body 를 가져오지 않는 방법으로 일단 우회를 했다.  
주말동안 좀 더 알아보고 나서 회사가서 직접 webView 와 함께 테스트를 진행해 봐야할듯 하다.  
월요일날 신입분들 스터디 진행을 위해 공부를 정리해 가야겠다.

#2022.03.06

주말동안 기획서 검토하고 가족과 좋은 시간도 보냈다.  
회사 신입분들과 부사수 같은 분에게 월요일날 진행중인 프로젝트의 코어부분의 한 부분을 설명하고,  
어떠한 기술인지, 어떠한 요건에 의해 이렇게 구성하였고, 소스코드 리뷰 정도 진행 후,  
앞으로의 공부방법이라던지, 당부의 말을 전하고 싶다.  
최소한 같이 일할려면 이정도는 알아야 한다 정도를 알려주고싶다.  
물론 나도 잘 알고 잘 하는건 아니겠지만, 최소한의...내가 무엇인가를 요청하고 정확히 포인트를 집어주면 어설프게나마 구현이 가능할 정도로..  
갈 길이 멀구나..다들 힘내자! 나도!! 님들도!!

#2022.03.08

오늘은 신입분들 프로젝트 구성부분 설명해 드렸다.  
앞으로 신입분들에게 어떻게 효율적으로 스터디 또는 강의형식으로 알려드려야할지 고민해 봐야겠다.  
기초를 튼튼히 만들어야겠다, 나도 기초부분이 약한부분이 있으니 좀 더 공부하고 일석이조!!

#2022.03.09
공부는 계속 하겠지만 꾸준히 깃헙은 잠시 못올릴 수 있겠다라는 생각이 들었다..  
오늘 대표님이랑 면담을 진행했는데 내쪽 프로젝트가 더디다는 얘기를 듣고 멘붕이 왔다.. 
내가 너무 완성도만 높인거 같아 죄송스럽기도하고,,  
오자마자 인수인계 하나 없이 그냥 스스로 찾아서 해야한다는것도 좀 서럽고..  
하.지.만 이러한 야생같은 환경이 날 더 강하게 만들지..후후...  
그래서 내일부터는 빡겜모드로 들어가려한다..  
다시 일 중복이...프로젝트 끝날때 까지는 주말이고..쉬는날에도..일을 좀 해야겠다..  
다행히 신입분들도 잘 도와주는거 같아 기분이 좋았다...ㅋㅋ  
할말은 있으나, 피곤하니 여기까지 일기 끝~~  
씁씁하고..달달한 밤이네..


#2022.03.12
주말동안 마무리 작업 하면서, 다른분들 commit 된 코드들을 보게되었는데, 기분이 썩 좋치는 않았습니다.  
내 방식이 전부 맞는건 아니겠지만, 내가 주의를 주고, 반드시 지켜야할 부분의 포인트 들을 알려주었는데, 
1개도 지켜지지 않아, 고민이 깊어졌다.  
내가 가르키고자 하는 의지와, 내가 가고자하는 방식을 강요하는게 아닌가 싶은 생각이 들었다.  
나도 신입시절을 돌아보게되고, 생각해 보면 마이웨이의 길을 걷을때가 있었던거 같다.  
하지만, 내가 아는 선에서는 최선을 다한거같은데..  이러식의 프로그래밍을 하게된다면, 정말 서비스 다 망가지는 지름길 같은데.. 
내가 모자르고 꼰대같고, 신용이 없어서 그런걸까, 어떡게 다가가서 좋은 방향으로 프로그래밍의 가이드와 습관을 기르게 해줄지 모르겠다..   
다들 바빠서인지, 내가 말하면 귀찮아 하는거같고..    
열심히 들은거 같은데, 막상 보면 지켜진건 없고..  
내가 모자라서, 좀 더 쉽고 명확하게 전달을 못한거 같아서 속상하다.  
정말 팀을 키우고싶고 회사를 키우고싶은 욕심은 많은데, 나만 유별나게 큰일인듯처럼 말하는거 같고..  
내가 볼때 진짜 심각한데, 다들 의연한거보니 내가 잘못된건가 싶기도하고..  
내가 원하는 회사는 이런게 아닌데 싶기도하고..  
그냥 나만, 내가 원하는 길로 가되, 다른분들은 덜 신경쓰고 사고가나거나 속도가 느려지면 그때 리펙터링을 해야할까..  
내가 잘못인거 같은데.. 어디서 부터 어떻게 풀어야 할지..  욕심을 좀 버려야 할지..  
정말 코더는 안되었으면 해서 소통의 일부라 생각했는데, 다들 귀찮은걸까..   
사람마다 다른거 같아 속상하다.  
그냥 나는 공부나 하러 가야겠다.

#2022.03.16
요즘 상당히 바쁘고..이상하게 몸이 너무 무겁다..  
공부는 하고있는데, 소스코드보다는 다시 기초를 공부중에 있다.  
요즘 기초가 튼튼해야 한다는게 와닿는 하루하루 여서,, jpa 부터 다시 기초,,jpa 훑어보고, 자료구조 쪽 조금 살펴볼 생각이다.  
시큐리티 쪽도 flow 한번 더 살펴볼 예정이고, 배치도 공부해야할듯한데..음...스프링 기초도 다시 공부해야하고..  
허허..기초 공부는 게을리하면 안되는걸 다시 깨닫는다 ㅠㅠ..  

#2022.03.21
아이고 바쁘다..짧게나마 tdd 를 공부하고있고, Real MySQL 8.0 세트(개정판)을 회사에 부탁해서 하나 사야겠다..  
좀 늦은감이 있지만, 디비를 좀 봐야겠다.. 요즘 디비공부를 안한지 오래되서..쪼매 힘드네..  jpa 는 요즘 공부를 한 덕에 그다지 어렵진 않다.  
아직 큰 장애 이슈를 만난건 아니지만, 크게 걱정할 필요는 없는것 같다.  다만.. 디비설계와 테이블 설계를 내가 좀 하고싶다는 욕심이 있다.  
내 스타일이 아닌지라 연관관계라던지 테이블 설계가 힘들다..ㅎㅎ 

#2022.03.25
오늘은 QueryDsl 부분에서 신박한 이슈를 만남..  
table 명이 order 가 있고, right  2개의 예약어를 쓰는(mysql) 테이블이 있는데, order 테이블은 select from 으로 잘 불러와 지는 반면,  
right 는 못불러오고 exception 이 계속 발생하였다.  
결론은 order 는 Qfile 을 만들면서 order1 이라는 alias 가 만들어 지는 반면 right 는 right 라고 변환없이 만들어 지고 있어서,  
결국  val right = QRight("right1") 같은 별칭을 따로 주었다.  
또 하나를 배움 ㅎㅎ 개발팀장님 떙큐요!! :)  

