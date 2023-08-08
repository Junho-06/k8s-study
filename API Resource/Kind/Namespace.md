### 네임스페이스란
쿠버네티스 상의 API 오브젝트들을 논리적으로 구분하여 관리하고 싶을 때  
분류뿐만 아니라 해당 논리적인 그룹에 대하여 권한 관리, CPU & Memory 등 리소스 제한 등을 하고 싶을 때 사용하는 API 리소스 입니다.

- 리소스를 논리적으로 나누기 위한 방법을 제공합니다. (논리적인 그룹)
- 네임스페이스의 단위는 사용자 목적에 맞추어 결정합니다.

### 네임스페이스 범위 API 리소스
네임스페이스에 속할 수 있는 리소스를 네임스페이스 범위 API 리소스 라고합니다.
- Pod, Deployment, Service, Ingress, Secret, ConfigMap, ServiceAccount, Role, RoleBinding 등

### 클러스터 범위 API 리소스
클러스터 범위의 API 리소스들을 말합니다 (네임스페이스에 속하지 않는 API 리소스이기도 함)
- Node, Namespace, IngressClass, PriorityClass, ClusterRole, ClusterRoleBinding

### 쿠버네티스의 기본 네임스페이스
쿠버네티스 클러스터를 생성하고나면 기본적으로 만들어지는 네임스페이스 종류

1. default
- 네임스페이스를 지정하지 않은 경우에 기본적으로 할당되는 네임스페이스 입니다.

2. kube-system
- 쿠버네티스 시스템에 의해 생성되는 API 오브젝트들을 관리하기 위한 네임스페이스 입니다.

3. kube-public
- 클러스터 내 모든 사용자로부터 접근 가능하고 읽을 수 있는 오브젝트들을 관리하기 위한 네임스페이스 입니다.

4. kube-node-lease
- 쿠버네티스 클러스터 내 노드의 연결 정보를 관리하기 위한 네임스페이스 입니다.

### 네임스페이스 단위의 자원 사용량 관리를 할 수 있는 API 리소스
- ResourceQuota
    - 네임스페이스에서 사용할 수 있는 자원 사용량의 합을 제한합니다.
    - 할당할 수 있는 자원(CPU, Memory, Volume 등)의 총합을 제한할 수 있습니다.
    - 생성할 수 있는 리소스(Pod, Service, Deployment 등)의 개수를 제한할 수 있습니다.

- LimitRange
    - 파드 혹은 컨테이너에 대하여 자원 기본 할당량 설정, 혹은 최대 / 최소 할당량 설정이 가능합니다.