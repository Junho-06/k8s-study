## 쿠버네티스 클러스터 구성요소
쿠버네티스의 클러스터 구성요소는 크게 2가지로 나뉩니다

1. Control Plane (Master Node)

    - 클러스터의 관리 역할을 담당합니다.
    - 상태 관리 및 명령어 처리를 수행합니다.

2. Node (Worker Node)

    - 어플리케이션 컨테이너를 실행합니다.

### Control Plane 구성요소
1. API Server

    - 쿠버네티스 리소스와 클러스터 관리를 위한 API를 제공합니다.
    - etcd를 데이터 저장소로 사용합니다.

2. Scheduler
    
    - 노드의 자원 사용 상태를 관리하며, 새로운 워크로드를 어디에 배포할지 관리합니다.

3. Controller Manager

    - 여러 컨트롤러 프로세스를 관리합니다.
    - 각 컨트롤러는 클러스터로부터 특정 리소스 상태의 변화를 감지하여 클러스터에 반영하는 reconcile 과정을 반복 수행합니다.

    - kube Controller Manager, cloud Controller Manager로 나눠지며 cloud Conroller Manager는 클라우드 provider에서 작업한 기능을 수행합니다. (ex: AWS의 ALB)

4. etcd

    - 분산 Key - Value 저장소로 클러스터의 상태를 저장합니다.

### Node 구성요소
1. kubelet

    - 컨테이너 런타임과 통신하며 컨테이너 라이프사이클을 관리합니다.
    - API 서버와 통신하며 노드의 리소스를 관리합니다.

2. CRI (Container Runtime Interface)

    - kubelet이 컨테이너 런타임과 통신할 때 사용되는 인터페이스 입니다.
    - 쿠버네티스는 Docker, containerd, cri-o 컨테이너 런타임을 지원합니다.

3. kube-proxy

    - 오버레이 네트워크를 구성합니다.
    - 네트워크 프록시 및 내부 로드밸런서 역할을 수행합니다.