<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/f9fd8831-4b9c-4d0a-8451-238332e2e6eb">

이번 아키텍처 설계는 Redis를 이용해 Server Side Caching을 Client Side Caching으로 변경하는 과정에서 설계한 내용입니다. 

기존 온라인 쇼핑몰 ver.2에서 RDBMS에서 정적 데이터를 요청하는 것을 Redis를 도입해 RDBMS의 부하를 30퍼센트 이상 낮춘 경험이 있습니다. 

이번에 프로젝트를 ver.6로 업그레이드 하는 과정에서 Redis를 이용해 Client Side Caching을 프로젝트에 접목시켰고 이를 통해 애플리케이션과 Redis가 소통하기위해 필요한 리소스를 아낌으로서 Redis에 가해지는 부하를 줄일 수 있었습니다. 

Client Side Caching을 적용함으로써 Latency는 평균 80% 최대 130% 개선하였고, throughput은 평균 4% 최대 250% 개선하였습니다.

## 장점
- Redis에 요청하는 네트워크 비용이 발생하지 않습니다.
- 데이터를 응답하기위한 Redis의 부하가 발생하지 않습니다.
- Latency를 개선할 수 있습니다.
- Throughput을 높일 수 있습니다.

## 단점
- 로컬 캐시는 관리하기 까다로워 신중하게 사용해야합니다. 
- Server Side Caching에 비해 생각해야하는 경우의 수가 늘어나 애플리케이션의 복잡도가 증가합니다.

## 느낀점
제가 여태껏 해본 경험 중 서버를 증설하거나 수직적 확장을 제외하고 코드레벨의 개선을 통해 서버의 전체적인 성능이 개선된 첫 사례였습니다.

또한, 비교적 최신 기술인 Redis6를 이용해 트랜드를 따라가는 경험을 하게 되었습니다. 이전엔 기존에 있던 기술들을 공부하는 느낌이었다면 최신기술의 동향을 파악하는데 좋은 경험이 되었던 것 같습니다. 

업데이트된 캐시데이터와 로컬 캐시의 싱크를 맞춘다는 점에서 만약 Redis Clustering을 진행했을 때 마스터 노드만 바라보면 되기 때문에 높은 HA상황에서도 Redis의 성능을 개선하는데 좋은 전략이 될 것 같습니다.

- [Redis for Client Side Caching 이론](https://coding-review.tistory.com/524)
- [Redis for Client Side Caching 실습](https://coding-review.tistory.com/525)
- [Redis for Client Side Caching 성능테스트](https://coding-review.tistory.com/528)
