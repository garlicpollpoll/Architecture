<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/dde95e87-723e-40d4-9f71-2ba19c3b3e7b">

기존 온라인 쇼핑몰 ver.2에서 동시성 문제가 발생하여 이를 JPA의 Pessimistic Lock을 이용해 해결했습니다. 

하지만 이러한 방식은 RDBMS가 Lock을 관리하는 과정에서 커넥션을 생성하기 때문에 RDBMS로 향하는 트래픽에 악영향을 줄 것이라고 판단하였습니다. 

이를 해결하기위해 Redis의 분산락을 이용해 RDBMS가 Lock을 관리하기위해 오롯이 부담했어야 할 부하를 Redis와 나눠 데이터베이스 커넥션 풀의 안정성을 높이고 부하를 낮춤으로서 장애상황을 방지할 수 있었습니다. 

[Pessimistic Lock -> Redis 분산락](https://coding-review.tistory.com/527)
[Redis 분산락 부하테스트](https://coding-review.tistory.com/529)
