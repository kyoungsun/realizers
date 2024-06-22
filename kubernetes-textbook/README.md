1주차 - 02장~06장
2주차 - 07장~11장
3주차 - 12장~16장
4주차 - 17장~21장



### 컨테이너(container)
* 애플리케이션 구성 요소 하나를 실행하는 가상화된 환경
* 같은 파드 안에서 실행되는 컨테이너는 같은 IP 주소를 공유함


### 파드(pod)
* 쿠버네티스가 하나 또는 그 이상의 컨테이너를 관리하는데 사용하는 단위
* 컴퓨팅의 단위로, 클러스터(cluster)를 이루는 노드 중 하나에서 실행됨
* 쿠버네티스로 관리되는 자신만의 가상 IP 주소를 가짐


### 디플로이먼트(deployment)
파드의 관리를 담당하는 리소스

### 네임스페이스(namespace)
쿠버네티스 단일 클러스터 내에서의 리소스 그룹 격리 메커니즘을 제공함

2024.06.09 TODO
1. minikube 설치
2. kubectx 설치
3. fzf 설치

*.yaml로 할 것


### 컨피그맵(ConfigMap)
파드에서 읽어 들이는 데이터를 저장하는 리소스

한 개 이상의 키-값 쌍, 텍스트, 바이너리 파일까지 다양한 데이터 형태를 지원

환경 변수
JSON, XML, YAML, TOML, INI 등 설정 파일
라이센스 키 전달

- 볼륨 마운트 경로가 이미 컨테이너 이미지에 있는 경로일 경우 컨피그맵 디렉터리가 원래 디렉터리를 덮어쓰기 때문에 애플리에키션 이상을 발생 시킬 수 있으므로 주의
- 외부에 유출하기 곤란한 민감한 설정 값은 사용 X


### 비밀값(Secret)
- 민감한 정보가 담긴 설정 값을 다룰 때 사용하는 리소스
- 해당 값을 사용해야 하는 노드에만 전달
- 노드에서도 디스크에 저장하지 않고 메모리에만 담김
- 비밀값도 컨테이너 안에서는 평문이 담긴 텍스트 파일이 됨
  - 비밀값을 환경 변수로 설정할 때 주의해야함
- 비밀값을 파일로 받는 방법을 통해 노출을 최소화 시킬 수 있음
- 비밀값을 yaml로 관리하는 것은 형상 관리 도구에 노출 될 수 있으므로 별도의 프로세스를 거칠 필요가 있음
  - 깃허브 시크릿 등등
- 