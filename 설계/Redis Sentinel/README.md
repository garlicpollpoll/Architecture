![Redis Sentinel Architecture](https://github.com/user-attachments/assets/b71b9f3d-33b2-4964-86bc-d68ac6d65867)

ver.2에서 Redis를 이용해 RDBMS의 부하를 30퍼센트 줄여 RDBMS의 장애 상황을 미연에 방지하였습니다. 

이후 ver.6에서 Redis를 이용한 Server Side Caching을 Client Side Caching으로 변경하면서 응답속도와 처리량을 높였습니다. 

하지만 이후 온라인 쇼핑몰의 특성상 읽기 연산이 자주 일어난다는 특성 때문에 Redis의 가용성을 높여야할 필요가 생겼습니다. 이를 해결하기 위해 추가적으로 Redis 서버를 두대 늘려 Replication을 진행했습니다. 

또한, 마스터 노드의 장애상황에 대비하기위해 슬레이브 노드를 마스터로 승경시키기위해 Redis에서 자체적으로 HA를 위해 제공하는 Redis Sentinel을 적용했습니다. 

이와 더불어 마스터노드의 장애상황에 알람을 받을 수 있도록 Redis Sentinel에서 기본적으로 제공해주는 Notification-Script를 이용했습니다.

## 장점
 - Redis의 고가용성
 - Sentinel을 통해 마스터노드의 장애상황에 대비해 데이터 유실을 최소화

## 아쉬운 점
 - 마스터 노드가 다운되고 슬레이브가 다음 마스터로 승격되는데 걸리는 시간이 길게는 5분정도 소요됨. 그 사이 Redis의 데이터 유실이 우려됨

## 느낀점
Redis의 Replication으로 읽기 연산을 분산시키고 Sentinel로 고가용성을 높이면서 Slack과의 연동으로 장애 상황에 즉각적으로 대응할 수 있었습니다. 

인프라를 구축하면서 실 서비스의 인프라는 이보다 더 복잡할 것인데 토이프로젝트 수준에서 미리 경험한 것이 실전에서 도움이 될 것이라고 믿고있습니다. 
