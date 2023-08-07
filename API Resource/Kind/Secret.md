### 시크릿이란
패스워드, API Key, SSH Key 등 민감한 정보를 컨테이너에 주입해야할 때 사용하는 API 리소스 입니다.

컨피그맵과 사용법이 비슷합니다.

시크릿은 사용 목적에 따라 몇 가지로 종류로 나누어 집니다.

쿠버네티스는 기본적으로 시크릿 값을 저장할 때 Base64로 인코딩하여 저장합니다.

접근 권한 설정이 중요한 리소스입니다. (ex: RBAC [ Role Based Access Control ])

컨테이너에 볼륨 , 환경변수로 주입이 가능합니다.

### 시크릿의 종류
1. Opaque (generic) - 일반적인 용도의 시크릿
2. dockerconfigjson - 도커 이미지 저장소 인증 정보
3. tls - TLS 인증서 정보
4. service-account-token - ServiceAccount의 인증 정보