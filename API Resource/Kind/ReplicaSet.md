### 레플리카셋이란?
정해진 수의 파드가 항상 실행될 수 있도록 관리해주는 서비스입니다.

기존 실행중이던 파드에 문제가 생기면 파드를 다시 스케줄링 합니다.

파드와 마찬가지로 레플리카셋을 직접 관리하는 경우는 거의 없습니다.

### 레플리카셋의 동작원리
ReplicaSet Controller가 Control Plane에 존재합니다.

spec.selector에 대응되는 파드의 수가 spec.replicas와 동일한지 지속적으로 검사하고, 다를 경우 스케일 아웃 혹은 스케일 인을 진행합니다.

- 레이블 셀렉터?
    
    - 쿠버네티스 오브젝트는 모두 metadata.lebels에 Key - Value 형태의 레이블 값을 가집니다.
    - 특정 오브젝트 목록을 필터링하기위한 기능이 Label Selector 입니다.
    - matchLabels와 matchExpressions 옵션을 제공합니다.
    - 많은 쿠버네티스 API 리소스가 Label Selector을 통해 기능을 제공합니다.
        - 이로 인해 리소스 간의 느슨한 결합을 유지합니다.