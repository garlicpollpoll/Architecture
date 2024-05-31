# 블루그린 배포

## ⚙️ Architecture Design

<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/4889059c-229d-4e21-ba38-204760570b8a">

<img src="https://github.com/garlicpollpoll/Architecture/assets/86602266/ae7e8fec-6af2-4017-a6c6-254f30b671b6">

### 특이사항

 - git push를 하면 Jenkins가 배포를 자동으로 처리해줍니다.
 - github에 있던 build.gradle을 빌드하여 JAR파일을 생성합니다.
 - JAR파일을 docker build를 이용하여 이미지로 만듭니다.
 - 이미지를 docker hub에 저장합니다.
 - deploy.sh에서 docker hub에 있던 이미지를 가져와 docker-compose.yml 파일을 실행시킵니다.

블로그 포스팅
[프로젝트에 블루그린 배포 적용하기](https://coding-review.tistory.com/411)
[무중단 배포 방법론](https://coding-review.tistory.com/408)
[무중단 배포 과정](https://coding-review.tistory.com/410)

### 블루그린 배포 선택 이유
무중단 배포를 진행함에 있어서 고려사항이었던 롤링 배포, 블루 그린 배포, 카나리 배포 중 블루 그린 배포를 선택한 이유는 다음과 같습니다. 

 - 롤링 배포는 서버의 개수가 많은 상황에서 유리하다고 판단하였습니다.
 - nginx가 제공하는 로드밸런싱 알고리즘 특성상 카나리 배포는 불가능하다고 판단하였습니다. 카나리 배포에 대해 찾아보니 쿠버네티스같은 컨테이너 관리 툴이 카나리 배포가 가능한 것으로 파악되어 너무 오버 엔지니어링이라 판단하였습니다.

최종적으로 블루그린 배포가 더 적합해서 프로젝트에 적용했다기보단 롤링 배포, 카나리 배포가 프로젝트와 어울리지 않아 블루 그린 배포를 진행하였습니다.  
