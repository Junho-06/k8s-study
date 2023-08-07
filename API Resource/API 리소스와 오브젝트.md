### API 리소스
API 리소스는 쿠버네티스가 관리할 수 있는 오브젝트의 종류를 말합니다.

- Pod, Service, ConfigMap, Secret
- Node, ServiceAccount, Role

### 오브젝트
오브젝트는 API 리소스를 인스턴스화 한 것을 말합니다.

즉 API 리소스는 오브젝트에 대한 명세이며 객체지향의 Class 느낌이고 오브젝트는 Class를 구현한 객체 같은 느낌입니다.

### 관련 명령어
`kubectl api-resources` : 현재 쿠버네티스 클러스터가 지원하는 API 리소스 목록을 출력합니다.

`kubectl explain {api resource name}` : 특정 api 리소스에 대해 간단한 설명을 볼수 있습니다.