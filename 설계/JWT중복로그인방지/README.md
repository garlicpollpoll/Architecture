# JWT 중복 로그인 방지

## ✔️ JWT 인증 흐름도
<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/fe56be83-2084-48df-9adc-9d4803a7743e">

기존 JWT 흐름도에서 Access Token (이하 AT) 이 만료되는 상황에서 로그인을 유지하기위해 Refresh Token (이하 RT) 를 확인하고 AT를 재발급하는 과정을 거쳤습니다. 

문제는 만약 아직 AT가 발급되어있는 상황에서 재로그인을 시도하는 상황에서 문제가 발생할 수 있습니다. 

이는 JWT로 인증을 구현하는 과정에서 서버는 인증과정에서 디커플링되어 생기는 문제입니다. 

## ⚙️ JWT 중복 로그인 방지 아키텍처
<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/409f2e83-410d-434b-b4be-72f1b16c64be">

기존에 클라이언트 앞에 있던 JWT 필터 뒤에 AT를 인증하기위한 중복로그인 방지 필터를 하나 더 두어 중복로그인을 방지하였습니다. 

이 중복로그인 방지 필터는 쿠키에 저장되어있는 클라이언트만의 고유값을 이용해 AT를 Redis에서 검색해 존재하면 로그인페이지로 이동하는 필터입니다. 

### 장점
- 중복로그인을 방지할 수 있다.

### 단점
- 애플리케이션의 규모가 커서 서버가 여러대이고 Redis가 여러대인 상황이라면 AT의 동기화를 신경써야 할 것입니다.
- 데이터베이스와 연결하여 AT를 확인해야하기 때문에 Redis의 CPU부하가 예상됩니다.
- 데이터베이스에 AT를 확인하는 과정에서 Network I/O에 대한 리소스를 사용해야합니다.

## 📈 느낀점
- 아키텍처를 고민하면서 다양한 환경변수를 고려하는 방법에 대해서 알게 되었습니다.
- 기존에 JWT와 스프링 시큐리티를 결합해 만든 프로젝트를 경험삼아서 더 나아가 중복로그인을 고려하면서 회사 서비스에 적용할 수 있었습니다.
- JWT가 stateless라고 알고 있었는데 구현하는 과정에서 stateful하게 구현할 수 밖에 없다는 것에 대해 진지하게 고찰해보고 이에 대해 생각을 정리하는 시간을 가질 수 있었습니다.

## 블로그
- [JWT와 Spring Security 결합하기](https://coding-review.tistory.com/382)
- [JWT는 진정 stateless인가?](https://coding-review.tistory.com/511)
- [JWT 중복로그인 방지](https://coding-review.tistory.com/512)

