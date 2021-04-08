## 200216

### Kubernetes

* pod(파드): 여러 컨테이너가 모인 서비스 or 하나의 컨테이너로 구성되어있음(즉 하나 이상)
* cluster(클러스터): 운영하는(배포하는) 하나의 형태
* helm(헬름): 
  1. 클러스터 각 환경에 따라 달라지는 값을 정해두고 이에 따라 배포하는 매커니즘.
  2. 쿠버네티스 차트를 관리하기 위한 도구
* 차트: 매니페스트 템플릿 구성하고 패키지로 관리, 매니페스트 파일 생성

* 매니페스트: 매니페스트 파일에 기초해 쿠버네티스 리소스 관리

* 실무에서는 로컬 및 운영 클러스터를 막론하고 여러 환경에 배포해야하기 때문에 애플리케이션은 모두 차트로 패키징해 kubectl 대신 helm으로 배포 및 업데이트.