# 3 Tier Architecture

## ⚙️ Architecture Design

<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/215fe2eb-23ea-4947-a697-7536d095fc76">

이 프로젝트는 흔히 사용하는 3티어 아키텍처를 AWS를 이용해 고도화하는 프로젝트입니다. 

### 특이사항

 - WAF를 이용해 방화벽을 세워 DDoS의 공격을 방어할 수 있습니다.
 - 애플리케이션이 위치한 EC2와 데이터베이스가 위치한 EC2를 모두 내부망으로 넣어두고 ALB만 외부로 노출하였습니다. 또한, 애플리케이션이 위치한 EC2의 SG를 로드밸런서로 두고 데이터베이스가 위치한 EC2의 SG를 22번과 3306번만을 두어 보안상 이점을 가져갈 수 있었습니다.
 - 로드밸런싱 알고리즘을 Least Connection으로 설정하여 동적으로 트래픽을 분산시킬 수 있게 조절하였습니다. 
 - 데이터베이스의 유실과 폭발적으로 트래픽이 발생할 경우를 대비하여 Replica를 하나 두었습니다.
 - 데이터베이스의 접근을 KMS와 Secret Manager를 이용해 관리하였습니다.
 - 폭발적인 트래픽에 ASG를 설정하여 유연성을 높였습니다.
 - EC2인스턴스에 Cloud Watch를 연결하여 알람을 받을 수 있게 하였습니다.

블로그 포스팅

* [AWS를 이용하여 3티어 아키텍처 고도화하기](https://coding-review.tistory.com/505)
