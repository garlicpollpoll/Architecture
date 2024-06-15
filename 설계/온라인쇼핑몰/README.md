# 온라인 쇼핑몰 (사이드 프로젝트)

# System Architecture
<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/66cd2ec5-716d-402c-9c96-77109a971cae">

## 설계시 중점사항
온라인 쇼핑몰 프로젝트는 실제 운영하고 있다는 가정하에 구현한 프로젝트입니다. 

그에따라 프로젝트를 구현하고 나서도 꾸준히 개발하여 고도화작업을 하였습니다. 현재는 ver.5까지 개발된 상태이고 추후 thymeleaf로 되어있는 프론트를 react로 마이그레이션하는 작업도 진행할 예정입니다. 

프로젝트를 구현할 때 중점적으로 두었던 사항입니다. 
- 사용자 경험을 위해 검색 성능을 개선하자. [링크](https://coding-review.tistory.com/391)
- 쿼리를 요청할 때 고정적으로 필요한 데이터를 캐싱하여 데이터베이스의 부하를 줄이자. [링크](https://coding-review.tistory.com/374)
- 조인연산이 많이 들어간 쿼리의 처리에 데이터베이스의 부하가 예상되니 replica를 한대 더 두자. [링크](https://coding-review.tistory.com/419)
- CPU 사용률, 메모리 점유율, JVM의 GC의 상태 등을 지속적으로 모니터링하여 문제가 될만한 곳을 찾아야한다. [링크](https://coding-review.tistory.com/439)
- 서버가 내려갔다 올라가는 과정에서 hard shutdown 되는 부정적인 경험을 최소화하자. [링크](https://coding-review.tistory.com/430)
- JVM 기반의 애플리케이션이 겪는 고질적인 문제인 JVM의 클래스로더 warm up과 JIT 컴파일러 warm up을 신경쓰자. [링크](https://coding-review.tistory.com/431)
- 사용자가 24시간 사용한다는 가정하에 지속적인 업데이트와 빠른 피드백 수용을 위해 무중단 배포를 진행하자. [링크](https://coding-review.tistory.com/411)
- 사용자가 많아 AWS의 ASG를 이용하는 경우 WAS서버가 여러대면 기존의 stateful한 인증 방식이 힘들 수 있으니 WAS서버의 인증 체계를 브라우저와 데이터베이스에 위임하자. [링크](https://coding-review.tistory.com/381)

구조적으로 프로젝트를 개선한 것 이외에도 추후 코드의 가독성과 확장성을 위해 리팩토링까지 진행하였습니다. [링크](https://coding-review.tistory.com/category/%EC%82%AC%EC%9D%B4%EB%93%9C%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8/%EC%98%A8%EB%9D%BC%EC%9D%B8%20%EC%87%BC%ED%95%91%EB%AA%B0%20ver.5)

## 느낀점
저는 실제 사용자가 없이 진행한 것이라 실제 서비스하는 것과 달라 부족할 수 있지만 실제 운영에서 생길 수 있는 문제에 대해 고민해보고 나름대로 해결방법을 생각하여 직접 프로젝트에 녹여냈습니다. 

과정에서 실제 서비스 되고 있는 모든 애플리케이션을 운영하는 개발자분들에 대한 존경심을 표할 수밖에 없었습니다. 

개인적으로 약 7개월정도 시간을 쓴 프로젝트인만큼 애정도 깊고 계속 고도화하고 싶습니다. 
