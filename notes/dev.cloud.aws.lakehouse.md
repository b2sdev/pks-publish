---
id: k5czowo3tsy1kbggabfgzsa
title: AWS Lake House
desc: ''
updated: 1693718664216
created: 1670631727791
---

## AWS 데이터 레이크, 분석 및 ML 서비스

![](https://d2908q01vomqb2.cloudfront.net/b6692ea5df920cad691c20319a6fffd7a4a766b8/2020/12/08/harness-the-power-5.jpg)

### 데이터 저장
#### **Amazon S3** 및 **Amazon Glacier**
Amazon S3 및 Amazon Glacier를 사용하여 데이터를 원하는 형식으로 안전하고 대량으로 편리하게 저장할 수 있음
- Amazon S3는 안전하고 확장이 가능하며 내구성이 우수한 객체 스토리지
- Amazon Glacier는 데이터 보관 및 백업용 스토리지를 제공하는 온라인 파일 스토리지 웹 서비스
- Amazon Glue는 최종 사용자가 분석을 위해 사용할 관련 데이터를 쉽게 찾을 수 있도록 사용자가 검색하고 쿼리할 수 있는 단일 카탈로그를 자동으로 생성

### 데이터 통합
#### **AWS Glue**
데이터 분석, 기계 학습 및 애플리케이션 개발을 위해 여러 소스에서 데이터를 쉽게 탐색, 준비, 이동 및 통합할 수 있도록 해줌
- 완전관리형 ETL(추출, 변환 및 로드) 서비스. AWS 관리 콘솔에서 클릭 몇 번으로 ETL 작업을 생성하고 실행할 수 있음
- 빅데이터 분석 시 다양한 데이터 소스에 대한 전처리 작업을 할 때, 별도의 데이터 처리용 서버나 인프라를 관리할 필요가 없음
#### **AWS Glue DataBrew**
데이터 분석가와 데이터 사이언티스트가 손쉽게 데이터를 정리 및 정규화하여 분석 및 기계학습을 위해 준비할 수 있도록 지원하는 시각적 데이터 준비 도구
- 사전 빌드된 250개 이상의 변환 구성 중에서 선택하여 코드 작성 없이도 데이터 준비 작업을 자동화할 수 있음
- 이상 항목 필터링, 표준 형식으로 데이터 변환, 잘못된 값 수정, 기타 작업을 자동화할 수 있음
- 데이터가 준비되면 분석 및 기계 학습 프로젝트에 바로 사용할 수 있음

### **데이터 분석**
#### **Amazon Athena**
대화형 분석을 위해 표준 SQL 쿼리를 사용하여 S3 및 Glacier에서 편리하게 데이터를 분석할 수 있도록 해줌
#### **Amazon EMR**
방대한 데이터를 편리하고 신속하며 비용 효과적으로 처리할 수 있는 관리형 서비스를 제공
#### **Amazon Redshift**
페타바이트 규모의 정형 데이터에 대한 복잡한 분석 쿼리를 실행할 수 있는 기능을 제공
- 불필요하게 데이터를 이동할 필요 없이 S3에서 엑사바이트 또는 더 작은 크기의 정형 또는 비정형 데이터에 대한 SQL 쿼리를 직접 실행하는 Redshift Spectrum을 포함하고 있음
#### **Amazon Kinesis**
IoT 텔레메트리 데이터, 애플리케이션 로그, 웹 사이트 클릭스트림 등과 같은 스트리밍 데이터를 편리하게 수집, 처리, 분석할 수 있도록 해줌
#### **Amazon Elasticsearch Service**
애플리케이션 모니터링, 로그 분석 및 클릭스트림 분석과 같은 운영 분석을 위해 사용<br>
거의 실시간으로 데이터를 검색, 탐색, 필터링, 집계, 시각화할 수 있음
#### **Amazon QuickSight**
비즈니스 분석 서비스를 제공<br>
시각화를 간소화하고, 모든 브라우저나 모바일 기기에서 액세스할 수 있는 강력한 대시보드를 제공

### 예측 분석
#### **AWS Deep Learning AMI**
ML 및 DL 최적화 GPU 인스턴스를 사용하여 편리하게 딥 러닝 모델을 개발하고 클러스터를 구축할 수 있음
#### **Amazon SageMaker**
ML을 심층적으로 활용하려는 개발자를 위해 학습 데이터를 연결하고 최상의 알고리즘과 프레임워크를 선택하고 최적화하며 Amazon EC2의 자동 확장 클러스터에 모델을 배포하기 위해 기업에 필요한 모든 것을 제공하여 ML 모델의 구축, 학습, 배포 프로세스를 간소화하는 플랫폼 서비스
- SageMaker에는 Amazon S3에 저장된 학습 데이터의 편리한 탐색과 시각화를 수행할 수 있도록 해주는 호스팅형 Jupyter 노트북도 포함됨
- 이미 만들어진 AI 기능을 앱에 연결하려는 개발자를 위해 컴퓨터 비전 및 자연어 처리를 위한 솔루션 지향 API를 제공

## AWS의 Lake House 접근 방식

<img src="https://d2908q01vomqb2.cloudfront.net/b6692ea5df920cad691c20319a6fffd7a4a766b8/2021/04/27/bdb809-build-a-lake-house-4.png" width=62%>

![](https://d2908q01vomqb2.cloudfront.net/b6692ea5df920cad691c20319a6fffd7a4a766b8/2020/12/08/harness-the-power-4.jpg)

## AWS의 Lake House Architecture

![](https://d2908q01vomqb2.cloudfront.net/b6692ea5df920cad691c20319a6fffd7a4a766b8/2021/04/07/bdb809-build-a-lake-house-2_1.jpg)

![](https://d2908q01vomqb2.cloudfront.net/b6692ea5df920cad691c20319a6fffd7a4a766b8/2021/04/07/bdb809-build-a-lake-house-3_1.jpg)

## Reference
- https://kr-resources.awscloud.com/data-resource-hub-kr/the-business-value-of-aws-data-lakes-analytics-and-ml-services-kr
- [Build a Lake House Architecture on AWS](https://aws.amazon.com/ko/blogs/big-data/build-a-lake-house-architecture-on-aws/)
- [Harness the power of your data with AWS Analytics](https://aws.amazon.com/ko/blogs/big-data/harness-the-power-of-your-data-with-aws-analytics/)
- [AWS Glue DataBrew로 기술 분석을 위한 데이터 세트 강화하기](https://www.megazone.com/techblog_220303/#)