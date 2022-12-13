
### What

- 쿠버네티스에서 컨테이너 애플리케이션의 기본 단위; 컨테이너를 표현하는 최소 단위
- 1개 이상의 컨테이너를 실행하는 컨테이너 그룹
- 클러스터의 노드에 배포되어 컨테이너 단위로 실행됨
- Pod 리소스는 클러스터 내에서 접근 가능한 고유의 IP를 가짐
- kubectl run(CLI) 명령 또는 YAML 파일을 이용해 생성

### Pod 생성 w/ YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-yml
spec:
  containers:
  - name: my-nginx-container
    image: nginx:latest
    ports:
    - containerPort: 80
      protocol: TCP
```

#### Pod 정의 구성 요소

구성 요소 | 설명
---|---
apiVersion  | 쿠버네티스 api의 버전을 가리킴
kind        | 어떤 리소스 유형인지 결정 (파드, 레플리카컨트롤러, 서비스 등)
metadata    | 파드와 관련된 이름 네임스페이스, 라벨 및 그 밖의 정보
spec        | 컨테이너 볼륨 등의 정보
status      | 파드의 상태, 각 컨테이너의 설명 및 상태, 파드 내부의 IP 및 그 밖의 기본 정보 등
