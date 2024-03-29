---
id: i72er7p7yb3mfelrn45f3i4
title: Solutions Architect 인터뷰 준비 - 기본 개념
desc: ''
updated: 1693730101539
created: 1693663938788
---

# 1. Infrastructure

<details>
<summary>인프라스트럭처를 구성할 때 IaaS, PaaS, SaaS의 차이점은 무엇이며 어떤 것을 선택해야 하는지 설명해주세요.</summary>
<div markdown="1">

- IaaS(Infrastructure as a Service): 가상화된 컴퓨팅 리소스를 제공합니다. 예: AWS EC2, Azure Virtual Machines.
- PaaS(Platform as a Service): 개발, 실행, 관리를 위한 플랫폼을 제공합니다. 예: AWS Elastic Beanstalk, Azure App Service.
- SaaS(Software as a Service): 클라우드 기반의 응용 프로그램을 제공합니다. 예: Google Workspace, Salesforce.
  
  선택은 특정 작업의 요구 사항, 관리의 용이성, 비용 효율성에 따라 결정됩니다.

</div>
</details>

<br />

<details>
<summary>온프레미스와 클라우드 인프라스트럭처의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- 온프레미스는 조직의 물리적인 위치에 설치된 인프라를 나타내며, 자체 서버와 데이터 센터에서 관리됩니다. 반면 클라우드 인프라는 서드파티 제공자가 호스팅하며, 인터넷을 통해 액세스됩니다.

</div>
</details>

<br />

<details>
<summary>높은 가용성을 위한 인프라 설계 전략은 무엇이 있나요?</summary>
<div markdown="1">

- 여러 데이터 센터나 가용 영역 간의 리소스 분산, 클러스터링, 로드 밸런싱, 자동 장애 복구, 백업 및 재해 복구 전략 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>Terraform과 CloudFormation의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- Terraform은 다양한 클라우드 제공자에 걸쳐 사용할 수 있는 Infrastructure as Code 도구입니다. 반면, CloudFormation은 AWS 전용입니다.

</div>
</details>

<br />

<details>
<summary>컨테이너와 VM의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- VM은 각각의 OS를 포함하며, 컨테이너는 호스트 OS의 일부를 공유하며 동작합니다. 따라서 컨테이너는 VM에 비해 가볍고 빠르게 시작됩니다.

</div>
</details>

<br />

<details>
<summary>인프라를 코드로 관리하는 이점은 무엇인가요?</summary>
<div markdown="1">

- 자동화, 일관성, 재사용 가능성, 문서화, 버전 관리 및 협업의 향상 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>성능 모니터링 도구를 사용하여 인프라의 어떤 측면을 모니터링 할 수 있나요?</summary>
<div markdown="1">

- CPU 사용률, 메모리 사용, 디스크 I/O, 네트워크 대역폭 및 지연 등을 모니터링할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>인프라 보안의 핵심 요소는 무엇인가요?</summary>
<div markdown="1">

- 방화벽, 암호화, 접근 제어, 감사 및 로깅, 보안 패치 및 업데이트 관리 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>하이브리드 클라우드 인프라스트럭처의 장점은 무엇인가요?</summary>
<div markdown="1">

- 유연성, 비용 효율성, 보안 및 규정 준수, 최적의 리소스 사용 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>인프라를 자동화하기 위해 어떤 도구나 기술을 사용할 수 있나요?</summary>
<div markdown="1">

- Terraform, Ansible, Chef, Puppet, Jenkins 등의 도구 및 기술을 사용하여 인프라를 자동화할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>RAID는 무엇인가요?</summary>
<div markdown="1">

- RAID(Redundant Array of Independent Disks)는 여러 개의 디스크를 하나의 논리적 단위로 묶어 데이터의 신뢰성과 성능을 향상시키는 기술입니다. RAID는 여러 가지 레벨(RAID 0, RAID 1, RAID 5 등)로 구성될 수 있으며, 각 레벨은 데이터 분배 및 복제 방식에 따라 다른 성능과 내구성 특성을 가집니다.

</div>
</details>

<br />

# 2. Networking

<details>
<summary>OSI 모델은 무엇이며, 각 계층을 설명해주세요.</summary>
<div markdown="1">

- OSI(Open Systems Interconnection) 모델은 네트워킹의 표준 모델로, 7개의 계층으로 구분됩니다. 물리, 데이터 링크, 네트워크, 전송, 세션, 표현, 응용 계층입니다. 각 계층은 특정한 네트워크 기능을 담당합니다.

</div>
</details>

<br />

<details>
<summary>TCP와 UDP의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- TCP는 연결 지향적이로 신뢰성 있는 통신을 제공합니다. 데이터 전송의 정확성을 확인합니다. 반면, UDP는 연결 없이 데이터를 전송하며, 신뢰성 보다는 속도를 중요시합니다.

</div>
</details>

<br />

<details>
<summary>NAT(Network Address Translation)의 역할은 무엇인가요?</summary>
<div markdown="1">

- NAT는 사설 IP 주소를 공인 IP 주소로 변환하는 과정을 말합니다. 이를 통해 여러 장치가 하나의 공인 IP 주소를 사용하여 인터넷에 접속할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>VPN이란 무엇이며, 어떻게 작동하나요?</summary>
<div markdown="1">

- VPN(Virtual Private Network)은 퍼블릭 네트워크를 통해 가상의 사설 네크워크 연결을 생성하는 기술입니다. 암호화를 사용해 데이터의 보안을 보장합니다.

</div>
</details>

<br />

<details>
<summary>CIDR 표기법이란 무엇인가요?</summary>
<div markdown="1">

- CIDR(Classless Inter-Domain Routing) 표기법은 IP 주소와 함께 서브넷 마스크의 길이를 나타내는 방법입니다. 예: `192.168.1.0/24`

</div>
</details>

<br />

<details>
<summary>Load Balancer의 역할과 종류에 대해 설명해주세요.</summary>
<div markdown="1">

- 로드 밸런서는 네트워크 트래픽을 여러 서버 간에 분산시키는 역할을 합니다. 주요 종류로는 L44(TCP/UDP 기반) 및 L7(HTTP/HTTPS) 로드 밸런서가 있습니다.

</div>
</details>

<br />

<details>
<summary>IPv4와 IPv6의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- IPv4는 32비트 주소 체계를 사용하며, IPv6는 128비트 주소 체계를 사용합니다. IPv6는 주소 공간이 훨씬 크므로 더 많은 장치에 IP 주소를 할당할 수 있습니다.

</div>
</details>

<br />
<details>
<summary>네트워크에서의 라우팅이란 무엇이며, 정적 라우팅과 동적 라우팅의 차이는 무엇인가요?</summary>
<div markdown="1">

- 라우팅은 데이터 패킷이 소스에서 목적지까지 어떤 경로를 통해 이동할지 결정하는 과정입니다. 정적 라우팅은 수동으로 경로를 설정하는 반면, 동적 라우팅은 라우팅 프로토콜을 사용하여 경로를 자동으로 결정합니다.

</div>
</details>

<br />

<details>
<summary>DNS(Domain Name System)의 역할은 무엇인가요?</summary>
<div markdown="1">

- DNS는 도메인 이름을 IP 주소로 변환하거나 IP 주소를 도메인 이름으로 변환하는 시스템입니다. 이를 통해 사용자는 IP 주소가 아닌 친숙한 도메인 이름을 사용하여 웹사이트에 접속할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>네트워크에서 패킷 흐름을 모니터링하려면 어떤 도구를 사용하나요?</summary>
<div markdown="1">

- 패킷 캡처 및 분석 도구인 Wireshark, tcpdump 등을 사용하여 네트워크의 패킷 흐름을 모니터링하고 분석할 수 있습니다.

</div>
</details>

<br />

# 3. AppDev

<details>
<summary>MVC 패턴이란 무엇이며, 왜 사용하나요?</summary>
<div markdown="1">

- MVC는 Model, View, Controller의 약자로, 애플리케이션의 구조를 세 부분으로 나눈 설계 패턴입니다. 이 패턴을 사용하면 애플리케이션의 관심사를 분리하여 유지보수와 확장성을 향상시킬 수 있습니다.

</div>
</details>

<br />

<details>
<summary>RESTful API란 무엇인가요?</summary>
<div markdown="1">

- RESTful API는 웹의 표준을 기반으로 데이터를 주고받은 설계 패러다임입니다. 이를 통해 자원에 URL을 부여하고 CRUD 연산을 HTTP 메서드(GET, POST, PUT, DELETE 등)로 수행합니다.

</div>
</details>

<br />

<details>
<summary>모바일 앱과 웹 앱의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- 모바일 앱은 특정 OS에 최적화되어 설치되며, 웹 앱은 브라우저를 통해 접근합니다. 모바일 앱은 일반적으로 웹 앱보다 더 빠르고 기능이 풍부하나, 업데이터나 배포가 복잡할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>앱의 성능을 향상시키기 위한 방법은 무엇이 있을까요?</summary>
<div markdown="1">

- 코드 최적화, 캐싱, 데이터베이스 질의 최적화, CDN 사용, 압축 알고리즘 사용 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>Dependency Injection이란 무엇이며, 왜 사용하나요?</summary>
<div markdown="1">

- Dependency Injection은 객체의 의존성을 외부에서 주입받는 패턴입니다. 이를 사용하면 코드의 유연성과 테스트 용이성을 향상시킬 수 있습니다.

</div>
</details>

<br />

<details>
<summary>Progressive Web Apps(PWA)의 장점은 무엇인가요?</summary>
<div markdown="1">

- PWA는 웹 앱을 모바일 앱처럼 사용할 수 있게 만듭니다. 오프라인 작동, 홈 화면 추가, 푸시 알림 등의 기능을 제공하며, 별도의 설치 없이 접근 가능합니다.

</div>
</details>

<br />

<details>
<summary>Single Page Application(SPA)이란 무엇이며, 어떤 장단점이 있나요?</summary>
<div markdown="1">

- SPA는 하나의 웹 페이지에서 모든 사용자 인터페이스를 제공하는 애플리케이션입니다. 페이지 리로드 없이 데이터를 동적으로 업데이트합니다. 장점으로는 빠른 사용자 경험이 있고, 단점으로는 초기 로딩 시간이 길 수 있습니다.

</div>
</details>

<br />

<details>
<summary>앱 개발에서 메모리 누수(memory leak)의 원인과 해결 방법은 무엇인가요?</summary>
<div markdown="1">

- 메모리 누수는 더 이상 필요 없는 객체에 대한 참조가 제거되지 않아 메모리 해제가 안 되는 현상입니다. 정기적인 코드 리뷰, 프로파일러 사용, 참조 제거 등으로 해결할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>앱의 반응성을 향상시키기 위한 방법은 무엇이 있을까요?</summary>
<div markdown="1">

- 비동기 프로그래밍, 캐싱, 데이터 로딩 최적화, UI 업데이트 최적화 등을 통해 반응성을 향상시킬 수 있습니다.

</div>
</details>

<br />

<details>
<summary>앱 개발에서 Unit Testing의 중요성은 무엇인가요?</summary>
<div markdown="1">

- Unit Testing은 개별 코드 단위의 기능을 테스트합니다. 이를 통해 코드의 품질을 보장하고, 변경 시 발생할 수 있는 문제점을 빠르게 파악하며, 리팩토링과 기능 추가를 안전하게 수행할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>3 tier 웹 애플리케이션의 정의와 구성방식은 어떤 것이 있을까요?</summary>
<div markdown="1">

- 3 tier 웹 애플리케이션은 프리젠테이션(Presentation), 로직(Business Logic), 데이터(Data)의 세 가지 계층으로 구성된 애플리케이션 아키텍처를 의미합니다.
    - 프리젠테이션 계층: 사용자 인터페이스(UI)와 관련된 부분입니다.
    - 로직 계층: 비즈니스 로직, 데이터 처리 및 API 서비스 등이 포함됩니다.
    - 데이터 계층: 데이터베이스와의 상호작용 및 데이터 저장과 관련된 부분입니다.
</div>
</details>

<br />


# 4. Security

<details>
<summary>암호화와 해시의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- 암호화는 데이터를 원래의 형태로 복호화(복원)할 수 있는 방식으로 변환하는 것입니다. 해시는 데이터를 고정된 길이의 값으로 변환하며, 이 과정은 일방향적이므로 복원이 불가능합니다.

</div>
</details>

<br />

<details>
<summary>DDoS 공격이란 무엇이며 어떻게 대비해야 하나요?</summary>
<div markdown="1">

- DDoS(Distributed Denial Of Service)는 여러 곳에서 대량의 트래픽을 발생시켜 서비스를 중단시키는 공격입니다. 대비방안으로 트래픽 모니터링, 웹 방화벽, CDN 사용 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>OWASP Top 10이란 무엇인가요?</summary>
<div markdown="1">

- OWASP Top 10은 웹 애플리케이션 보안에 대한 취약점 목록 중 가장 위험한 10가지를 나열한 것입니다. 이를 통해 개발자와 기업들이 보안 위협에 대비할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>인증(Authentication)과 인가(Authorization)의 차이점은 무엇인가요?</summary>
<div markdown="1">

- 인증은 사용자의 신원을 확인하는 과정입니다. 인가는 해당 사용자에게 주어진 권한을 검증하는 과정입니다.

</div>
</details>

<br />

<details>
<summary>Man-in-the-Middle 공격이란 무엇이며, 어떻게 방어할 수 있나요?</summary>
<div markdown="1">

- Man-in-the-Middle 공격은 통신하는 두 당사자 사이에 중간에서 데이터를 가로채는 공격입니다. SSL/TLS 인증서를 사용하여 통신을 암호화하는 것으로 방어할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>SQL Injection이란 무엇이며 어떻게 예방할 수 있나요?</summary>
<div markdown="1">

- SQL Injection은 악의적인 SQL 코드가 데이터베이스에 직접 입력되어 실행되게 하는 공격입니다. 입력 값을 검증하거나, Prepared Statements를 사용하여 예방할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>Zero-Day 공격이란 무엇인가요?</summary>
<div markdown="1">

- Zero-Day 공격은 아직 발견되지 않은 취약점을 대상으로 하는 공격입니다. 이는 보안 패치가 나오기 전까지 알려지지 않습니다.

</div>
</details>

<br />

<details>
<summary>2-Factor Authentication(2FA)의 장점은 무엇인가요?</summary>
<div markdown="1">

- 2FA는 두 가지 인증 방법을 결합하여 보안을 강화합니다. 이를 통해 단순한 패스워드 유출만으로는 시스템에 접근하기 어려워집니다.

</div>
</details>

<br />

<details>
<summary>HTTPS의 기능과 중요성에 대해 설명해주세요.</summary>
<div markdown="1">

- HTTPS는 HTTP에 보안 계층을 추가한 것입니다. SSL/TLS를 사용하여 데이터를 암호화합니다. 이를 통해 중간자 공격과 데이터 탈취를 방지합니다.

</div>
</details>

<br />

<details>
<summary>보안 인증서(Certificates)와 키(Key)의 역할은 무엇인가요?</summary>
<div markdown="1">

- 보안 인증서는 기관의 신원을 증명하고 공개 키를 포함하며, 키는 암호화와 복호화 과정에서 사용됩니다. 개인 키는 비밀로 유지되며, 공개 키는 인증서와 함께 공개됩니다.

</div>
</details>

<br />

<details>
<summary>웹방화벽이 일반 방화벽과 어떻게 다른가요?</summary>
<div markdown="1">

- 웹방화벽(WAF, Web Application Firewall)은 주로 HTTP 트래픽을 모니터링하며 웹 애플리케이션의 보안을 강화하기 위해 설계되었습니다. 이는 SQL 인젝션, 크로스 사이트 스크립팅(XSS)과 같은 고유의 웹 위협을 탐지하고 차단합니다. 반면 일반 방화벽은 네트워크 트래픽을 모니터링하여 악성 트래픽을 차단하며, 주로 포트와 IP 주소를 기반으로 작동합니다.

</div>
</details>

<br />

# 5. Database & Analytics

<details>
<summary>RDBMS와 NoSQL 데이터베이스의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- RDBMS는 정규화된 구조와 고정된 스키마를 가지며, ACID 트랜잭션을 지원합니다. 반면, NoSQL은 스키마가 유연하고, 대규모 분산 데이터를 처리하는 데 적합합니다.

</div>
</details>

<br />

<details>
<summary>데이터 웨어하우스와 데이터 레이크의 차이점은 무엇인가요?</summary>
<div markdown="1">

- 데이터 웨어하우스는 구조화된 데이터를 위한 중앙 집중식 저장소입니다. 데이터 레이크는 구조화 및 비구조화 데이터 모두를 원시 형식으로 저장하는 대규모 저장소입니다.

</div>
</details>

<br />

<details>
<summary>OLAP와 OLTP의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- OLTP는 온라인 트랜잭션 처리를 위한 시스템으로, 실시간 데이터 입력, 수정, 검색을 지원합니다. OLAP는 온라인 분석 처리를 위한 시스템으로, 복잡한 질의와 데이터 분석에 최적화되어 있습니다. (cf. [[dev.cs.database.oltp-vs-olap]])

</div>
</details>

<br />

<details>
<summary>데이터 정규화의 주요 목적은 무엇인가요?</summary>
<div markdown="1">

- 데이터 중복성을 최소화하고, 데이터의 무결성을 향상시키며, 데이터베이스의 구조적 효율성을 증가시키는 것입니다.

</div>
</details>

<br />

<details>
<summary>Sharding이란 무엇이며, 어떤 장점이 있나요?</summary>
<div markdown="1">

- Sharding은 데이터를 여러 데이터베이스나 서버에 분할 저장하는 전략입니다. 이를 통해 읽기/쓰기 성능을 향상시키고, 확장성을 증가시킬 수 있습니다.

</div>
</details>

<br />

<details>
<summary>캐싱의 목적과 사용 시 주의할 점은 무엇인가요?</summary>
<div markdown="1">

- 캐싱은 자주 접근되는 데이터나 연산 결과를 빠르게 재사용하기 위한 기법입니다. 단, 캐싱된 데이터의 만료와 일관성 관리에 주의해야 합니다.

</div>
</details>

<br />

<details>
<summary>비정규화(De-normalization)의 목적과 장단점은 무엇인가요?</summary>
<div markdown="1">

- 비정규화는 읽기 성능을 향상시키기 위해 데이터의 중복성을 허용하는 것입니다. 장점은 쿼리 성능 향상이며, 단점은 데이터 관리의 복잡성 증가입니다.

</div>
</details>

<br />

<details>
<summary>ETL 과정이란 무엇인가요?</summary>
<div markdown="1">

- ETL은 '추출(Extract)', '변환(Tranform)', '로드(Load)'의 약자로, 데이터 웨어하우스에 데이터를 가져오고, 가공하고, 저장하는 과정을 의미합니다.

</div>
</details>

<br />

<details>
<summary>데이터 마이닝이란 무엇이며, 어떤 응용 분야에서 사용되나요?</summary>
<div markdown="1">

- 데이터 마이닝은 대규모 데이터에서 의미 있는 패턴이나 관계를 발견하기 위한 기법입니다. 시장 분석, 고객 세그멘테이션, 추천 시스템 등에서 사용됩니다.

</div>
</details>

<br />

<details>
<summary>인덱싱이란 무엇이며, 어떻게 데이터베이스에 성능을 향상시키나요?</summary>
<div markdown="1">

- 인덱싱은 데이터베이스에서 데이터를 빠르게 조회하기 위한 자료구조입니다. 인덱스를 사용하면 특정 데이터를 빠르게 찾아 접근할 수 있어 쿼리 성능이 향상됩니다.

</div>
</details>

</br>

<details>
<summary>Hadoop은 무엇인가요?</summary>
<div markdown="1">

- Hadoop은 대규모 데이터 세트를 처리하기 위한 오픈소스 프레임워크입니다. 분산 저장 시스템인 HDFS(Hadoop Distributed File System)와 맵리듀스(MapReduce)라는 프로그래밍 모델을 기반으로 하며, 대용량 데이터를 여러 개의 머신에 분산하여 저장하고 처리하는 데 효과적입니다.

</div>
</details>

<br />

<details>
<summary>열 지향(Column-oriented) 데이터베이스와 행 지향(Row-oriented) 데이터베이스의 주요 차이점은 무엇이며, 어떤 상황에서 열 지향 방식이 유리한가요?</summary>
<div markdown="1">

열 지향 데이터베이스는 데이터를 열 기반으로 저장하며, 행 지향 데이터베이스는 데이터를 행 기반으로 저장합니다.

- 열 지향 데이터베이스의 장점:
    - 데이터 압축: 같은 데이터 타입의 값들이 연속적으로 저장되기 때문에 압축 효율이 더 좋습니다.
    - 집계 쿼리 성능: 특정 열(들)만을 대상으로 하는 집계나 연산이 필요할 때, 행 전체를 읽는 것보다 훨씬 빠르게 동작합니다.
- 행 지향 데이터베이스의 장점:
    - 트랜잭션 처리 성능: 단일 레코드의 CRUD 작업이 빠르며, 특히 레코드 추가나 수정에 유리합니다.

열 지향 방식은 대용량 데이터에서 특정 열에 대한 집계나 분석 작업이 주로 필요한 OLAP(Online Analytical Processing) 같은 분석 쿼리에 유리하며, 행 지향 방식은 OLTP(Online Transaction Processing) 시스템에서 더 흔히 사용됩니다.

</div>
</details>

<br />

<details>
<summary>Columnar storage의 주요 장점은 무엇인가요?</summary>
<div markdown="1">

- 데이터 압축: 동일한 데이터 타입의 값들이 같은 열에 연속적으로 저장되므로 더 효율적인 압축이 가능합니다.
- 쿼리 성능 향상: 쿼리는 필요한 열만 읽을 수 있으므로 I/O 작업이 줄어들고, 이는 집계 및 분석 쿼리의 성능을 크게 향상시킵니다.
- 스캔 속도: 특정 열의 데이터만 읽어들이기 때문에 전체 행을 읽는 것보다 스캔 속도가 빠릅니다.
- 비용 효율성: 더 나은 압축률과 I/O 최적화로 인해 저장 공간 및 쿼리 비용이 절약됩니다.

</div>
</details>

<br />

<details>
<summary>데이터 웨어하우스에서 Star Schema와 Snowflake Schema의 차이점은 무엇인가요?</summary>
<div markdown="1">

- Star Schema와 Snowflake Schema는 두 가지 주요 데이터 웨어하우스 스키마 설계 방식입니다.
- Star Schema:
    - 중심에 큰 "fact table"이 위치하고, 이 테이블에 직접 연결된 차원 테이블(dimension tables)로 구성됩니다.
    - 차원 테이블은 정규화되지 않은 형태입니다.
    - 쿼리 성능이 뛰어나며, 직관적이어서 이해하기 쉽습니다.
- Snowflake Schema:
    - Star Schema의 확장 형태로, 차원 테이블이 추가적으로 분해되어 정규화된 형태로 저장됩니다.
    - 데이터 중복성이 줄어들고, 저장 공간을 더 효율적으로 사용할 수 있습니다.
    - 그러나 복잡한 조인으로 인해 쿼리 성능에 영향을 줄 수 있습니다.
- 따라서 Star Schema는 간단하고 빠른 성능을 원할 때, Snowflake Schema는 저장 공간의 효율성과 데이터의 일관성을 원할 때 선택될 수 있습니다.

</div>
</details>

<br />

<details>
<summary>ETL과 ELT 프로세스의 주요 차이점을 설명하고, 각 프로세스의 장점 및 적절한 사용 시나리오에 대해 설명해 주십시오.</summary>
<div markdown="1">

- ETL(Extract, Transform, Load):
    - 정의: ETL은 데이터를 원본 소스에서 추출하고, 변환 프로세스를 거쳐 원하는 형식으로 만든 후, 목표 데이터 웨어하우스에 로드하는 과정을 의미합니다.
    - 장점:
        - 미리 변환된 데이터를 데이터 웨어하우스에 로드하기 때문에, 일단 데이터가 로드되면 쿼리 성능이 빠릅니다.
        - 원본 데이터의 품질이나 일관성에 문제가 있을 경우, 변환 단계에서 해당 문제를 해결할 수 있습니다.
        - 전통적인 관계형 데이터베이스 시스템에 잘 맞습니다.
    - 적절한 사용 시나리오: 구조화된 데이터를 가진 전통적인 데이터 웨어하우스 환경에서의 데이터 처리와 통합.
- ELT(Extract, Load, Transform):
    - 정의: ELT는 데이터를 원본 소스에서 추출한 후, 먼저 목표 데이터 웨어하우스에 로드하고, 데이터 웨어하우스 내에서 필요한 변환 작업을 수행하는 과정을 의미합니다.
    - 장점:
        - 현대의 데이터 웨어하우스 솔루션은 대용량의 데이터 변환 작업을 빠르게 처리할 수 있으므로 ELT가 가능합니다.
        - 데이터 로딩 후 변환을 수행하기 때문에, 다양한 형식의 데이터를 빠르게 데이터 웨어하우스에 가져올 수 있습니다.
        - 데이터 웨어하우스에서 직접 변환을 수행하기 때문에, 변환 로직을 쉽게 변경하거나 업데이트할 수 있습니다.
    - 적절한 사용 시나리오: 빅데이터 및 클라우드 기반 데이터 웨어하우스 환경, 데이터 웨어하우스 내에서 다양한 형식의 데이터를 동적으로 변환 및 집계해야 할 때.
- 요약하면, ETL은 데이터 변환의 복잡성을 처리하기 위해 중앙에서 데이터를 변환하는 반면, ELT는 데이터 웨어하우스의 스케일 및 처리 능력을 활용하여 변환을 수행합니다.
</div>
</details>

<br />

# 6. Machine Learning & Artificial Intelligence

<details>
<summary>머신러닝과 딥러닝의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- 머신러닝은 알고리즘을 사용하여 데이터에서 패턴을 학습하는 방법론입니다. 딥러닝은 머신러닝의 하위 집합으로, 심층 신경망(Deep Neural Networks)을 활용하여 학습하는 방식을 의미합니다.

</div>
</details>

<br />


<details>
<summary>과적합(Overfitting)이란 무엇이며, 어떻게 방지할 수 있나요?</summary>
<div markdown="1">

- 과적합은 모델이 훈련 데이터에 너무 잘 맞아서 실제 데이터에서는 일반화되지 않는 현상을 의미합니다. 교차 검증, 드롭아웃, 정규화 등의 방법으로 과적합을 방지할 수 있습니다.

</div>
</details>

<br />


<details>
<summary>회귀와 분류의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- 회귀는 연속적인 값을 예측하는 반면, 분류는 주어진 카테고리 중 하나로 데이터를 구분하는 작업입니다.

</div>
</details>

<br />


<details>
<summary>손실 함수(Loss Function)의 목적은 무엇인가요?</summary>
<div markdown="1">

- 손실 함수는 모델의 예측값과 실제값 사이의 차이를 측정하는 함수입니다. 이 차이를 최소화하도록 모델을 학습시킵니다.

</div>
</details>

<br />


<details>
<summary>랜덤 포레스트(Random Forest) 알고리즘의 주요 특징은 무엇인가요?</summary>
<div markdown="1">

- 랜덤 포레스트는 여러 개의 의사결정트리를 조합하여 작동하는 앙상블 기법입니다. 이는 과적합을 방지하고 예측의 정확도를 향상시킵니다.

</div>
</details>

<br />


<details>
<summary>Gradient Descent란 무엇이며, 어떻게 작동하나요?</summary>
<div markdown="1">

- Gradient Descent는 손실 함수의 기울기를 사용하여 최소값을 찾는 최적화 알고리즘입니다. 기울기의 반대 방향으로 파라미터를 업데이트하여 손실을 점차 줄여나갑니다.

</div>
</details>

<br />


<details>
<summary>특성 추출(Feature Extraction)과 특성 선택(Feature Selection)의 차이점은 무엇인가요?</summary>
<div markdown="1">

- 특성 선택은 중요한 특성을 선택하고 불필요한 특성을 제거하는 과정입니다. 특성 추출은 원래의 특성을 사용하여 새로운 특성을 생성하는 과정입니다.

</div>
</details>

<br />

<details>
<summary>정밀도(Precision)과 재현율(Recall)의 차이점은 무엇인가요?</summary>
<div markdown="1">

- 정밀도는 모델이 True라고 예측한 것 중 실제로 True인 것의 비율입니다. 재현율은 실제 True 중에서 모델이 True라고 예측한 것의 비율입니다.

</div>
</details>

<br />

<details>
<summary>Transfer Learning의 주요 장점은 무엇인가요?</summary>
<div markdown="1">

- Transfer Learning은 사전에 학습된 모델의 지식을 새로운 작업에 적용하는 방식입니다. 이를 통해 적은 양의 데이터로도 빠르고 효과적인 학습이 가능합니다.

</div>
</details>

<br />

<details>
<summary>심층 신경망에서 활성화 함수(Activation Function)의 역할은 무엇인가요?</summary>
<div markdown="1">

- 활성화 함수는 신경망의 각 뉴런의 출력값을 결정합니다. 이는 비선형성을 추가하여 모델의 표현력을 높여줍니다.

</div>
</details>

<br />

<details>
<summary>특성 공학(Feature Engineering)의 중요성은 무엇이며, 효과적인 특성 공학을 위한 주요 전략은 무엇인가요?</summary>
<div markdown="1">

- 특성 공학은 머신러닝에서 데이터를 모델에 입력하기 전에 데이터의 원시 특성을 변환하거나 새로운 특성을 생성하는 과정입니다. 올바른 특성을 선택하고 구성하는 것은 모델의 성능에 결정적인 영향을 미칠 수 있습니다.

- 특성 공학의 중요성:
    1. 성능 향상: 적절한 특성을 사용하면 모델의 학습 능력과 예측 성능이 향상될 수 있습니다.
    2. 학습 시간 단축: 불필요한 특성을 제거하거나 데이터의 차원을 줄이면 모델의 학습 시간을 줄일 수 있습니다.
    3. 이해력 향상: 중요한 특성을 파악하면 문제 도메인에 대한 통찰력을 얻을 수 있으며, 모델의 예측을 더 잘 이해할 수 있습니다.
- 효과적인 특성 공학을 위한 주요 전략:
    1. 도메인 지식 활용: 문제 도메인에 대한 지식을 활용하여 데이터에 숨겨진 패턴이나 관계를 반영하는 특성을 생성할 수 있습니다.
    2. 다양한 변환 시도: 로그 변환, 폴리노미얼 특성, 상호 작용 특성 등 다양한 수학적 변환을 시도해보는 것이 좋습니다.
    3. 특성 스케일링: 모든 특성이 동일한 스케일에 있도록 조정합니다. 예를 들면, 정규화(Normalization) 또는 표준화(Standardization)를 사용할 수 있습니다.
    4. 특성 선택: 중요한 특성만을 선택하여 차원의 저주를 피하고 과적합을 방지할 수 있습니다.
    5. 자동 특성 생성: 딥러닝과 같은 방법을 사용하여 데이터로부터 자동으로 특성을 추출할 수 있습니다.
- 결론적으로, 특성 공학은 모델의 성능을 최적화하는 데 중요한 역할을 합니다. 적절한 특성을 선택하고 구성하는 방법은 해당 문제와 사용되는 데이터에 따라 달라집니다.

</div>
</details>

<br />

<details>
<summary>편향(Bias)과 분산(Variance)의 차이점은 무엇이며, 이들이 모델 성능에 미치는 영향에 대해 설명해 주십시오.</summary>
<div markdown="1">

- 편향과 분산은 머신 러닝에서 모델의 성능과 오버피팅(overfitting) 혹은 언더피팅(underfitting) 문제를 이해하는 데 중요한 개념입니다.

- 편향 (Bias):
    - 편향은 모델의 예측값과 실제 값 사이의 평균적인 차이를 나타냅니다.
    - 높은 편향은 모델이 너무 단순하다는 것을 의미하며, 데이터의 복잡성을 충분히 잡아내지 못할 때 발생합니다. 이를 언더피팅이라고 합니다.
- 분산 (Variance):
    - 분산은 모델이 학습 데이터의 작은 변동에 얼마나 민감하게 반응하는지를 나타냅니다.
    - 높은 분산은 모델이 학습 데이터에 과도하게 적합하게 되어 새로운 데이터나 테스트 데이터에 대한 성능이 떨어지는 경우를 의미합니다. 이를 오버피팅이라고 합니다.
- 모델 성능에 미치는 영향:
    - 편향이 높고 분산이 낮은 경우: 모델이 너무 단순하여 데이터의 복잡성을 포착하지 못하는 상황을 나타냅니다. 이 경우, 더 복잡한 모델을 사용하거나, 추가적인 특성(feature)을 포함시키는 것으로 개선할 수 있습니다.
    - 편향이 낮고 분산이 높은 경우: 모델이 학습 데이터에 너무 잘 적합되어 있어, 새로운 데이터에 대한 성능이 떨어지는 상황을 나타냅니다. 정규화(regularization) 기법을 사용하거나, 데이터를 더 많이 모으는 것으로 개선할 수 있습니다.
- 보통 모델의 복잡도가 증가하면 분산은 증가하고 편향은 감소하는 경향이 있습니다. 따라서, 머신 러닝에서는 이 두 가지 문제 사이의 균형을 잘 찾는 것이 중요합니다. 이를 **편향-분산 트레이드오프(Bias-Variance Tradeoff)**라고 합니다.

</div>
</details>

<br />

<details>
<summary>정규화(Regularization)란 무엇이며, 이를 사용하는 이유는 무엇인가요?</summary>
<div markdown="1">

- 정규화(Regularization)는 머신 러닝 모델의 학습 과정에 추가되는 페널티 항목으로, 모델의 가중치가 너무 큰 값을 갖지 않도록 제한하는 기법을 의미합니다. 이는 모델의 과적합(overfitting)을 방지하는데 도움을 줍니다.

- 정규화의 주요 목적과 이유는 다음과 같습니다:

    1. 과적합 방지: 모델이 학습 데이터에 너무 정확하게 적합되어 새로운 데이터에 대한 일반화 성능이 떨어지는 상황, 즉 과적합을 방지하기 위해 사용됩니다.

    2. 모델 복잡도 제한: 정규화는 모델의 가중치에 대한 제약을 추가함으로써 모델의 복잡도를 제한합니다. 이로 인해 모델이 학습 데이터의 노이즈나 불필요한 패턴에 적합하는 것을 방지할 수 있습니다.

    3. 특성 선택: 일부 정규화 기법은 불필요한 특성의 가중치를 0으로 만들어 모델에서 해당 특성을 사용하지 않게 할 수 있습니다. 이를 통해 더 간단하고 해석하기 쉬운 모델을 얻을 수 있습니다.

- 대표적인 정규화 기법에는 L1 정규화 (Lasso)와 L2 정규화 (Ridge)가 있습니다. L1은 특성의 수를 줄이는 효과가 있어 특성 선택에 유용하며, L2는 가중치의 제곱항을 페널티로 사용하여 모든 특성에 일관된 제약을 가합니다.

</div>
</details>

<br />


<details>
<summary>어텐션(Attention) 메커니즘의 역할은 무엇이며, 자연어 처리에 있어서의 그 중요성에 대해 설명해 주십시오.</summary>
<div markdown="1">

- 어텐션 메커니즘은 딥러닝 모델, 특히 순환 신경망(RNN)과 트랜스포머(Transformer) 아키텍처에서 중요한 역할을 하는 기술입니다. 기본적으로 어텐션 메커니즘은 입력 데이터의 다양한 부분에 가중치를 부여함으로써 모델이 중요한 정보에 집중할 수 있게 도와줍니다.

- 어텐션의 핵심 역할:
    1. 가중치 부여: 입력 시퀀스의 각 요소에 대한 가중치를 계산하여, 모델이 어떤 부분에 더 집중해야 하는지 결정합니다.
    2. 중요한 정보 선택: 모든 입력 정보가 동등하게 중요하지 않기 때문에, 어텐션은 중요한 정보에 대해 높은 가중치를 부여합니다.

- 자연어 처리에서의 중요성:

    1. 시퀀스-투-시퀀스 모델링 향상: 예를 들어, 번역에서 소스 문장의 특정 단어나 구에 대한 타겟 문장의 단어 간의 관계를 명확하게 학습할 수 있습니다.
    2. 긴 의존성 학습: 전통적인 RNN은 긴 시퀀스에서의 의존성을 잘 학습하는 데 어려움이 있습니다. 어텐션 메커니즘을 통해 이러한 문제를 완화할 수 있습니다.
    3. 인터프리터빌리티 향상: 어텐션 가중치를 시각화하면 모델이 특정 출력을 생성하기 위해 어떤 입력 부분에 집중하는지 이해하기 쉽습니다.

- 결론적으로, 어텐션 메커니즘은 딥러닝 모델이 입력 데이터의 중요한 부분에 집중하도록 도와주며, 특히 자연어 처리 태스크에서 성능 향상과 모델의 해석 가능성을 높이는 데 중요한 역할을 합니다.

</div>
</details>

<br />



# 7. Virtualization

<details>
<summary>가상화(Virtualization)란 무엇인가요?</summary>
<div markdown="1">

- 가상화는 물리적 자원을 여러 개의 가상 환경으로 분리하는 기술입니다. 이를 통해 하나의 물리적 하드웨어 위에서 여러 운영체제나 애플리케이션을 동시에 실행할 수 있게 됩니다.

</div>
</details>

<br />

<details>
<summary>하이퍼바이저(Hypervisor)란 무엇이며, 그 종류는 무엇인가요?</summary>
<div markdown="1">

- 하이퍼바이저는 가상화 환경에서 여러 가상 머신(VM)을 실행하고 관리하는 소프트웨어 또는 하드웨어입니다. 주로 Type 1(베어 메탈) 하이퍼바이저와 Type 2(호스트 기반) 하이퍼바이저로 분류됩니다.

</div>
</details>

<br />

<details>
<summary>가상화의 주요 이점은 무엇인가요?</summary>
<div markdown="1">

- 자원 최적화, 높은 유연성, 개발 및 테스팅 편의성, 재해 복구 용이성, 서버의 운용 및 유지 비용 절감 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>오버커밋(Overcommit)이란 무엇이며, 왜 주의해야 하나요?</summary>
<div markdown="1">

- 오버커밋은 물리적으로 사용 가능한 자원보다 더 많은 가상 자원을 할당하는 것을 의미힙니다. 과도한 오버커밋은 성능 저하 및 가상 머신 간의 자원 경쟁을 초래할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>컨테이너와 VM(Virtual Machine)의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- VM은 전체 운영체제를 포함하므로 무거운 반면, 컨테이너는 OS 커널을 공유하므로 경량화되어 있습니다. 따라서 컨테이너는 VM보다 빠르게 시작되고, 더 적은 자원을 사용합니다.

</div>
</details>

<br />

<details>
<summary>가상 머신의 스냅샷(Snapshot) 기능의 장점과 단점은 무엇인가요?</summary>
<div markdown="1">

- 스냅샷은 특정 시점의 가상 머신 상태를 캡처합니다. 이를 통해 실패나 문제 발생 시 빠르게 원래 상태로 복원할 수 있습니다. 단, 너무 많은 스냅샷이 누적되면 성능 저하와 스토리지 사용량 증가의 문제가 발생할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>서버 가상화와 네트워크 가상화의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- 서버 가상화는 하드웨어 서버 자원을 가상 서버로 분리하는 것이며, 네트워크 가상화는 물리적 네트워크 자원을 여러 가상 네트워크로 분리하는 것입니다.

</div>
</details>

<br />

<details>
<summary>가상화에서 "파티셔닝(Partitioning)"과 "아이솔레이션(Isolation)"의 의미는 무엇인가요?</summary>
<div markdown="1">

- 파티셔닝은 하나의 물리적 자원을 여러 개의 독립된 부분(파티션)으로 나누는 것을 의미하며, 아이솔레이션은 각 파티션끼리의 상호 작용을 제한하여 독립성을 보장하는 것을 의미합니다.

</div>
</details>

<br />

<details>
<summary>가상 스위치(Virtual Switch)란 무엇인가요?</summary>
<div markdown="1">

- 가상 스위치는 가상화 환경 내에서 가상 머신 간의 통신을 관리하는 네트워킹 컴포넌트입니다.

</div>
</details>

<br />

<details>
<summary>Paravirtualization이란 무엇이며, 이 방식의 장점은 무엇인가요?</summary>
<div markdown="1">

- Paravirtualization은 전체 하드웨어를 시뮬레이션하는 대신, 운영체제가 직접 하이퍼바이저와 상호 작용하도록 수정된 가상화 방식입니다. 이 방식은 성능 향상 및 오버헤드 감소의 장점이 있습니다.

</div>
</details>

<br />

# 8. Microservices Architecture
<br />

<details>
<summary>마이크로서비스 아키텍처란 무엇인가요?</summary>
<div markdown="1">

- [[dev.architecture.microservices]] 아키텍처는 하나의 큰 애플리케이션을 작고, 독립적인 서비스로 분리하는 설계 패러다임입니다. 각 서비스는 독립적으로 배포 및 확장이 가능하며, 특정 비즈니스 기능을 수행합니다.

</div>
</details>

<br />

<details>
<summary>모놀리식 아키텍처와 마이크로서비스의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- 모놀리식 아키텍처는 애플리케이션의 모든 구성 요소가 하나의 코드 베이스와 실행 단위로 통합된 구조입니다. 반면, 마이크로서비스는 애플리케이션을 여러 독립적인 서비스로 분리합니다.

</div>
</details>

<br />

<details>
<summary>마이크로서비스 아키텍처의 주요 이점은 무엇인가요?</summary>
<div markdown="1">

- 확장성, 빠른 배포와 반복, 서비스 독립성, 기술 스택 유연성, 장애 격리 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>마이크로서비스에서는 서비스 간의 통신을 어떻게 처리하나요?</summary>
<div markdown="1">

- 주로 HTTP/REST, gRPC, 메시징 큐 등의 방식을 사용하여 서비스 간 통신을 처리합니다.

</div>
</details>

<br />

<details>
<summary>서비스 디스커버리(Service Discovery)란 무엇이며, 왜 중요한가요?</summary>
<div markdown="1">

- 서비스 디스커버리는 마이크로서비스 환경에서 서비스의 위치와 메타데이터를 동적으로 찾고 관리하는 과정입니다. 서비스의 확장성과 동적 환경 대응을 위해 필요합니다.

</div>
</details>

<br />

<details>
<summary>마이크로서비스에서는 데이터 관리에 어떤 접근 방식을 취하나요?</summary>
<div markdown="1">

- 마이크로서비스에서는 각 서비스가 자신의 데이터베이스를 갖는 '데이터베이스 퍼 서비스' 패턴을 추천합니다. 이를 통해 서비스의 독립성과 확장성을 보장합니다.

</div>
</details>

<br />

<details>
<summary>API Gateway의 역할은 무엇인가요?</summary>
<div markdown="1">

- API Gateway는 클라이언트와 마이크로서비스 간의 중간 계층으로, 요청/응답의 라우팅, 인증, 인가, 로드 밸런싱, 캐싱, 요율 제한 및 모니터링 등의 기능을 제공합니다.

</div>
</details>

<br />

<details>
<summary>Circuit Breaker 패턴의 목적은 무엇인가요?</summary>
<div markdown="1">

- Circuit Breaker는 연속된 실패 후 일정 시간 동안 서비스 호출을 중단하여 시스템의 과부하를 방지하고, 복구 시간을 확보하는 패턴입니다.

</div>
</details>

<br />

<details>
<summary>마이크로서비스에서의 로깅와 모니터링의 중요성에 대해 설명하십시오.</summary>
<div markdown="1">

- 분산된 여러 서비스에서 발생하는 문제를 신속하게 진단하고 해결하기 위해 통합된 로깅과 모니터링이 필수적입니다. 이는 서비스의 건강 상태를 파악하고, 장애 원인을 추적하는데 중요한 역할을 합니다.

</div>
</details>

<br />

<details>
<summary>마이크로서비스 아키텍처의 주요 단점은 무엇인가요?</summary>
<div markdown="1">

- 데이터 일관성 유지의 어려움, 서비스 간의 복잡한 통신, 분산된 시스템의 복잡성, 트랜잭션 관리의 어려움 등이 있습니다.

</div>
</details>

<br />

# 9. Containerization

<details>
<summary>컨테이너(Container)란 무엇인가요?</summary>
<div markdown="1">

- 컨테이너는 애플리케이션과 그에 필요한 모든 종속성 및 설정을 하나의 패키지로 캡슐화한 것입니다. 이를 통해 애플리케이션의 일관성 있는 실행 환경을 보장합니다.

</div>
</details>

<br />

<details>
<summary>Docker과 Kubernetes의 주요 차이점은 무엇인가요?</summary>
<div markdown="1">

- Docker는 컨테이너화된 애플리케이션을 만들고 실행하기 위한 플랫폼입니다. Kubernetes는 여러 Docker 호스트에서 컨테이너 클러스터를 자동화, 스케일링 및 관리하는 오케스트레이션 시스템입니다.

</div>
</details>

<br />

<details>
<summary>컨테이너 이미지와 컨테이너 인스턴스의 차이점은 무엇인가요?</summary>
<div markdown="1">

- 컨테이너 이미지는 애플리케이션과 그 종속성을 포함한 스냅샷이며, 컨테이너 인스턴스는 이 이미지를 기반으로 실행되는 실제 활성화된 환경입니다.

</div>
</details>

<br />

<details>
<summary>Docker Compose의 주요 역할은 무엇인가요?</summary>
<div markdown="1">

- Docker Compose는 멀티-컨테이너 Docker 애플리케이션의 정의와 실행을 단순화하기 위한 도구입니다. `docker-compose.yml` 파일을 통해 서비스, 네트워크, 볼륨 등을 정의할 수 있습니다.

</div>
</details>

<br />

<details>
<summary>컨테이너화의 주요 이점은 무엇인가요?</summary>
<div markdown="1">

- 일관된 환경, 빠른 배포, 확장성, 격리성, 리소스 효율성 등이 컨테이너화의 주요 이점으로 꼽힙니다.

</div>
</details>

<br />
<details>
<summary>컨테이너 런타임은 무엇인가요?</summary>
<div markdown="1">

- 컨테이너 런타임은 컨테이너의 실행과 관리를 담당하는 소프트웨어입니다. 예를 들면, Docker Daemon, containerd, runc 등이 있습니다.

</div>
</details>

<br />

<details>
<summary>Kubernetes의 Pod란 무엇이며, 이를 사용하는 주된 이유는 무엇입니까?</summary>
<div markdown="1">

- Pod는 Kubernetes에서 가장 작은 배포 단위로, 하나 이상의 컨테이너로 구성됩니다. Pod는 동일한 네트워크 네임스페이스 아래에서 실행되는 컨테이너의 그룹으로, 서로 밀접하게 연관된 컨테이너들을 함께 실행하기 위해 사용됩니다.

</div>
</details>

<br />

<details>
<summary>컨테이너의 스토리지 볼륨을 관리하는 데 있어서 주요 고려사항은 무엇인가요?</summary>
<div markdown="1">

- 데이터의 영속성, 볼륨의 생명 주기, I/O 성능, 백업 및 복원, 볼륨의 공유 여부 등이 주요 고려사항으로 꼽힙니다.

</div>
</details>

<br />

<details>
<summary>컨테이너 네트워킹의 주요 도전과제는 무엇인가요?</summary>
<div markdown="1">

- 서비스 발견, 로드 밸런싱, 네트워크 격리, 인그레스 및 이그레스 트래픽 관리, 네트워크 보안 등이 컨테이너 네트워킹의 주요 도전과제로 꼽힙니다.

</div>
</details>

<br />

<details>
<summary>`Dockerfile`이란 무엇이며, 어떻게 사용하는가요?</summary>
<div markdown="1">

- `Dockerfile`은 Docker 이미지를 빌드하기 위한 스크립트 파일입니다. 여기에는 이미지를 생성하기 위한 명령어와 설정이 포함되어 있으며, `docker build` 명령어로 Docker 이미지를 빌드할 때 사용됩니다.

</div>
</details>