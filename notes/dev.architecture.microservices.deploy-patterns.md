---
id: rlenn47khmjb6uyso6rzm27
title: 마이크로서비스 배포 패턴
desc: ''
updated: 1693722503294
created: 1693720823756
---

## 1. 언어에 특정한 패키징 포맷 패턴
언어에 특정한 패키지 형태로 프로덕션에 배포한다.

장점:
- 배포가 빠름
- 리소스를 효율적으로 활용할 수 있음(특히 같은 머신이나 같은 프로세스 내에서 여러 인스턴스를 실행할 때)

단점:
- 기술 스택을 캡슐화할 수 없음
- 서비스 인스턴스가 소비하는 리소스를 제한할 방법이 없음
- 여러 서비스 인스턴스가 동일 머신에서 실행될 경우 서로 격리할 수 없음
- 서비스 인스턴스를 어디에 둘지 자동으로 결정하기 어려움

> 서비스를 언어에 특정한 패키지로 배포하는 방법은 서비스가 아주 소수인 경우를 제외하면 가급적 삼가는 것이 좋습니다.

## 2. 가상 머신 패턴
서비스를 VM 이미지로 묶어 프로덕션에 배포한다. 각 서비스 인스턴스가 하나의 VM이다.

장점:
- VM 이미지로 기술 스택을 캡슐화
- 서비스 인스턴스가 격리됨
- 성숙한 클라우드 인프라를 활용함

단점:
- 리소스를 효율적으로 활용할 수 없음
- 배포가 비교적 느림
- 시스템 관리 오버헤드가 발생함

> 작고 간단한 애플리케이션이라면 국이 도커 오케스트레이션 프레임워크를 설정하지 말고 가상 머신으로 배포하는 것이 더 쉽습니다.

## 3. 컨테이너 패턴
서비스를 컨테이너 이미지로 묶어 프로덕션에 배포한다. 각 서비스 인스턴스가 곧 하나의 컨테이너다.

장점:
- 기술 스택의 캡슐화, 서비스 관리 API가 곧 컨테이너 API가 됨
- 서비스 인스턴스가 격리됨
- 서비스 인스턴스의 리소스를 제한할 수 있음

단점:
- 컨테이너 이미지를 직접 관리해야 하는 부담이 있음
- OS와 런타임 패치도 정기적으로 해주어야 함

> 어느 정도 서비스 개발이 진행되었다면, 쿠버네티스 같은 정교한 배포 인프라를 구성하는 것을 권장합니다.

## 4. 서버리스 패턴
퍼블릭 클라우드에서 제공하는 서버리스 배포 메커니즘을 이용하여 서비스를 배포한다.

장점:
- 다양한 AWS 서비스와의 연계
- 시스템 관리 업무가 많이 경감됨
- 탄력성
- 사용량만큼 과금

단점:
- 긴-꼬리 지연(long-tail latency)
- 제한된 이벤트/요청 기반 프로그래밍 모델