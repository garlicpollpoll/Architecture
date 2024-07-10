<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/f9fd8831-4b9c-4d0a-8451-238332e2e6eb">

이번 아키텍처 설계는 Redis를 이용해 Server Side Caching을 Client Side Caching으로 변경하는 과정에서 설계한 내용입니다. 

기존 온라인 쇼핑몰 ver.2에서 RDBMS에서 정적 데이터를 요청하는 것을 Redis를 도입해 RDBMS의 부하를 30퍼센트 이상 낮춘 경험이 있습니다. 

이번에 프로젝트를 ver.6로 업그레이드 하는 과정에서 Redis를 이용해 Client Side Caching을 프로젝트에 접목시켰고 이를 통해 애플리케이션과 Redis가 소통하기위해 필요한 리소스를 아낌으로서 Redis에 가해지는 부하를 줄일 수 있었습니다. 

Client Side Caching을 적용함으로써 Latency는 평균 80% 최대 130% 개선하였고, throughput은 평균 4% 최대 250% 개선하였습니다.

[Redis for Client Side Caching 이론](https://coding-review.tistory.com/524)
[Redis for Client Side Caching 실습](https://coding-review.tistory.com/525)
[Redis for Client Side Caching 성능테스트](https://coding-review.tistory.com/528)
