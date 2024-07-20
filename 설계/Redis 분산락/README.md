<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/dde95e87-723e-40d4-9f71-2ba19c3b3e7b">

기존 온라인 쇼핑몰 ver.2에서 동시성 문제가 발생하여 이를 JPA의 Pessimistic Lock을 이용해 해결했습니다. 

하지만 이러한 방식은 RDBMS가 Lock을 관리하는 과정에서 커넥션을 생성하기 때문에 RDBMS로 향하는 트래픽에 악영향을 줄 것이라고 판단하였습니다. 

이를 해결하기위해 Redis의 분산락을 이용해 RDBMS가 Lock을 관리하기위해 오롯이 부담했어야 할 부하를 Redis와 나눠 데이터베이스 커넥션 풀의 안정성을 높이고 부하를 낮춤으로서 장애상황을 방지할 수 있었습니다. 

또한, Redis가 RAM에서 동작하는만큼 속도가 빨라 데이터베이스 전체 부하의 20퍼센트정도 개선이 이루어졌습니다. 

## 장점
- RDBMS가 Lock을 관리하기위해 사용하던 리소스를 Redis와 나눠 가짐으로써 RDBMS가 장애상황이 될 가능성을 낮추는 효과를 가져올 수 있습니다.
- Redis의 Sorted Set 자료구조를 이용해 대기열을 구현하고 이를 비동기로 처리할 때 Redis의 분산락을 이용하여 동시성 문제를 해결할 수 있습니다.

## 단점
- Pessimistic Lock에 비해 성능적으로 조금 아쉬운 모습을 보여줬습니다. 안정성과 성능의 trade off 인 것 같습니다. 만약 Lock을 관리하는 RDBMS의 부하가 걱정되지 않는 상황이라면 사용하는 것이 성능적으로 부담될 수 있습니다.

## 느낀점
Redis를 공부하면서 Redis의 다양한 라이브러리와 다양한 자료구조덕분에 상당히 많은 것들을 Redis를 이용해 구현할 수 있다는 것을 알게되었습니다. 

조금 더 깊이있게 공부해보면서 어떤 부분이 사람들로하여금 Redis에 열광하게되는지 알게되는 뜻깊은 시간이었습니다. 

- [Pessimistic Lock -> Redis 분산락](https://coding-review.tistory.com/527)
- [Redis 분산락 부하테스트](https://coding-review.tistory.com/529)
