### 서비스란?
Deployment를 통해 파드를 수평확장 하면 트래픽은 어떻게 분산시킬지  
외부로부터의 요청을 받으려면 어떻게 해야하지 할 때 사용하는게 서비스 입니다.

- 여러 파드에 대해 클러스터 내에서 사용 가능한 고유 도메인을 부여합니다.
- 여러 파드에 대한 요청을 분산하는 로드 밸런서 기능을 수행합니다.
    - Ip / Port 기반의 L4 레이어의 로드밸런서 역할을 합니다.
- 파드의 IP는 항상 변할 수 있음에 유의 해야 합니다.
- 일반적으로는 ClusterIP 타입의 Service와 함께 Ingress를 사용하여 외부 트래픽을 처리합니다.
    - Ingress는 L7의 로드밸런서라고 생각합시다.

### ClusterIP Service
Service APi 리소스의 가장 기본적인 타입 입니다.

쿠버네티스 클러스터는 Pod에 부여되는 Pod IP를 위한 CIDR 대역과 Service에 부여되는 Cluster IP CIDR 대역이 독립적으로 존재합니다.

Label Selector를 통해 서비스와 연결할 파드 목록을 관리합니다.

Cluster IP 로 들어오는 요청에 대하여 파드에 L4 레벨의 로드밸런싱을 수행합니다.

Cluster IP 뿐만아니라 내부 DNS를 통해 서비스 이름을 이용한 통신이 가능합니다.

ClusterIP 타입의 Service는 쿠버네티스 클러스터 내부 통신 목적으로만 사용이 가능합니다.

### NodePort Service
모든 쿠버네티스 노드의 동일 포트를 개방하여 서비스에 접근하는 방식입니다.

NodePort는 Cluster IP 타입의 서비스를 한 번 더 감싸서 만들어진 것 입니다.

따라서 NodePort 서비스도 Cluster IP 사용이 가능합니다.

NodePort로 들어온 요청은 실제로 ClusterIP로 전달되어 Pod로 포워딩 됩니다.

### LoadBalancer Service
클라우드 프로바이더에서 제공하는 로드밸런서를 동적으로 생성하는 방식입니다.

LoadBalancer 타입 서비스는 NodePort 타입 서비스를 한 번 더 감싸서 만들어진 것입니다.

LoadBalancer 서비스도 Cluster IP 사용이 가능합니다.

LoadBalancer 서비스를 통해 만들어진 로드밸런서는 NodePort를 타겟 그룹으로 생성됩니다.

NodePort로 들어온 요청은 실제로 Cluster IP로 전달되어 Pod로 포워딩 됩니다.

AWS / GCP 등과 같은 클라우드 환경이 아니라면 기본적으로는 해당 기능이 이용 불가합니다.

MetalLB와 같은 기술 등을 사용하여 온프레미스 환경에서 LoadBalancer 타입 사용이 가능합니다.

### ExternalName Service
외부로 요청을 전달할 때 사용하는 서비스 입니다.

서비스가 파드를 가리키는 것이 아닌 외부 도메인을 가리키도록 구성이 가능합니다.

DNS의 CNAME 레코드와 동일한 역할을 수행합니다.

클러스터 외부에 존재하는 레거시 시스템을 쿠버네티스로 마이그레이션하는 과정에 활용이 가능합니다.