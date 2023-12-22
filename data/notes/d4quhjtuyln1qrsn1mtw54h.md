
![](https://contents.kyobobook.co.kr/sih/fit-in/458x0/pdt/9788931558111.jpg)

# 01. 클라우드 컴퓨팅과 AWS

## 01. 클라우드 컴퓨팅 개요

### 1. 클라우드 컴퓨팅
- 클라우드 컴퓨팅은 인터넷을 사용해서 자원(서버, 네트워크, 스토리지)을 사용할 수 있는 서비스

### 2. On-demand 서비스와 SLA
- 주문형(On-demand) 서비스: 클라우드 컴퓨팅 사용자가 요청한 만큼 서비스를 제공하고 비용을 청구하는 모델
- SLA(Service Level Agreement)
    - on-demand 서비스를 사용할 때 클라우드 컴퓨팅 서비스 사용자와 서비스 제공자(예: AWS) 간의 서비스 수준에 대한 협약서
    - SLA를 통해 사용자는 사용한 서비스만큼 비용을 지불

### 3. 가상화(Virtualization)
- 여러 개의 물리적 자원을 하나로 통합해서 관리하거나 하나의 물리적 자원을 여러 개로 분할하여 사용하는 기술
- 종류
    - 호스트 가상화
        - Host OS[^1] 위에 guest OS[^2]가 실행되는 방식
        - 예: VM Workstation, VMServer, Virtual Box
        - 단점: Host OS 위에 다시 guest OS를 설치해서 사용하기 때문에 오버헤드가 큼
    - 하이퍼바이저 가상화
        - Host OS가 없고 하드웨어에 하이퍼바이저라는 가상화 소프트웨어를 설치하여 사용하는 방식
        - 예: Xen, Microsoft Hyper-V, Citrix, KVM
        - 장점: Host OS가 없기 때문에 오버헤드가 적음
    - 컨테이너 가상화
        - Host OS 위에 컨테이너 관리 소프트웨어를 설치하여 논리적인 컨테이너를 나누어서 사용
        - 예: Docker
        - 장점: 오버헤드가 적고 속도가 빠름

## 02. 클라우드 컴퓨팅 모델

### 1. On-Premise
- 서버, 데이터베이스, 네트워크 장비 등을 모두 구매해서 구축하고 운영하는 서비스
- 일반적으로 IDC(Internet Data Center)에 서버를 설치하고 전용 네트워크를 통해서 운영하는 시스템 형태
### 2. 클라우드 컴퓨팅 종류
- Private Cloud: 기업 내부에서 기업 내부 조직원들을 위한 서비스를 제공
- Public Cloud: 인터넷을 사용해서 제공하는 클라우드 컴퓨팅 형태로 AWS, Azure 등이 있음
- Hybrid Cloud: Private 및 Public Cloud를 모두 제공하는 형태
### 3. 클라우드 컴퓨팅 모델
- IaaS(Infrastructure as a Service)
    - 인프라를 서비스 형태로 제공하는 것으로 서버, 스토리지, 네트워크 관련 각종 물리적 장비를 서비스 형태로 제공
    - AWS에서는 EC2, S3, VPC 등의 서비스
- PaaS(Platform as a Service)
    - 인프라에 설치되는 운영체제, 미들웨어, 데이터베이스 관리 시스템 등의 소프트웨어를 제공
    - AWS에서는 리눅스 및 윈도우 운영체제, Oracle, MySQL 등의 DBMS를 제공하는 것
- SaaS(Software as a Service)
    - 응용 프로그램을 서비스 형태로 제공하는 것
    - 구글 Office 365, 드롭박스 등의 응용 프로그램

## 03. AWS(Amazon Web Service)

### 1. AWS(Amazon Web Service)
AWS는 컴퓨팅, 네트워킹, 스토리지, 분석 플랫폼 등 다양한 서비스를 제공

#### 컴퓨팅 서비스

#### 네트워킹 서비스

#### 스토리지 서비스

#### 분석 플랫폼

#### 기타

### 2. AWS 장점

### 3. AWS 공동 책임 모델 및 규정 준수 프로그램
AWS 공동책임 모델이란 AWS와 클라우드 서비스 사용자(고객) 간에 책임을 정의한 모델

#### AWS 책임
- AWS 클라우드에서 제공되는 모든 서비스에 대해서 인프라를 보호할 책임
- 여기서 인프라란 하드웨어, 소프트웨어, 네트워킹 및 시설을 의미

#### 고객 책임
- AWS 내에 저장 및 관리하는 고객 데이터 관리(암호화), 자산 분류, 적절한 허가를 위한 IAM 도구, AWS EC2 인스턴스에 설치한 모든 애플리케이션 등은 고객 책임

### 4. AWS 사용 방법
#### AWS 인터페이스 방법
- AWS Management Console
- CLI(Command Line Interface)
- SDK(Software Development Kit)

### 5. 리전과 가용 영역
- 리전(Region): 전 세계에 있는 AWS의 데이터 센터의 물리적 위치
- 가용 영역(AZ; Availability Zone): 논리적 데이터 센터의 그룹

### 6. 요금 정책

## References
- [클라우드 AWS 자격증으로 시작하기](https://www.millie.co.kr/v3/bookDetail/179572928?referrer=searchRecent)

[^1]: Host OS: 하드웨어 위에 설치된 운영체제
[^2]: Guest OS: 호스트 가상화 혹은 하이퍼바이저 위에 설치된 운영체제