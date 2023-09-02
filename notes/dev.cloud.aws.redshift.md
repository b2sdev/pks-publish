---
id: vdibvlxx9sskn8p5g9tkqmh
title: Amazon Redshift
desc: ''
updated: 1693658555164
created: 1670637126767
---

## Amazon Refshift

### What
- AWS에서 제공되는 완전관리형 데이터 웨어하우스 서비스
    - 열 지향 데이터 저장 및 고급 쿼리 최적화 기법을 사용하여 빠른 쿼리 성능을 제공; Massively Parallel Processing(MPP) 아키텍처를 사용하여 대량의 데이터를 효과적으로 처리
- 표준 SQL을 사용하여 데이터를 간단하고 비용 효율적으로 분석할 수 있는 서비스
- 고성능 BI 보고서, 대시보드, 데이터 탐색 및 분석과 같은 분석 워크로드에 사용
- AWS 생태계와의 긴밀한 통합으로 인해 다양한 AWS 서비스(S3, Kinesis, Data Pipeline 등)와 원활하게 연동됨
- AWS의 보안 기능을 이용하여 데이터를 안전하게 보관하며, 암호화, VPC 통합, IAM을 통한 접근 관리 등 다양한 보안 기능을 제공
- 많은 사용자가 동시에 쿼리를 실행할 때 자동으로 리소스를 확장하여 대응 (Concurrency Scaling)

### How
#### Redshift로 데이터를 로딩하는 방법
- Amazon S3에 있는 데이터를 Redshift로 로딩할 때는 Redshift에서 **COPY** 명령 사용
- Amazon Kinesis로 인입되는 스트리밍 데이터의 경우 **Kinesis Firehose**를 사용하여 스트리밍 데이터를 직접 Redshift로 로드
    * Kinesis Firehose는 streaming data를 Amazon S3에 스테이지하고, 이를 Redshift에 COPY하는 것임
- **스트리밍 수집**을 사용하면 지연 시간이 짧고 빠른 속도로 Amazon Kinesis Data Streams에서 Amazon Redshift 구체화된 뷰로 스트림 데이터를 수집할 수 있음
    * 스트리밍 수집을 사용하면 데이터를 Kinesis Data Streams에서 Amazon Redshift 데이터베이스의 구체화된 뷰로 직접 전송할 수 있으므로 Amazon Kinesis Data Firehose 전송 스트림으로 데이터를 전송할 필요가 없음

## 스트리밍 수집
### What
- (준) 실시간 데이터 스트림을 낮은 지연 시간으로 Amazon Redshift에 로딩하기 위한 기능

### How
- Amazon Redshift 스트리밍 수집을 사용하면 Amazon S3에 데이터를 내리고 클러스터에 적재할 때 발생하는 적재 지연 시간과 복잡성 없이 Kinesis Data Streams에 직접 연결할 수 있음
- SQL을 사용하여 스트림 데이터에 연결하고 스트림을 기반으로 구체화된 뷰를 생성하므로 데이터 파이프라인이 단순해짐
    - 구체화된 뷰는 ELT(Extract(추출), Load(적재) 및 Transform(변환)) 파이프라인의 일부로 SQL을 이용한 데이터 변환도 할 수 있음
- 구체화된 뷰를 새로 고침으로 최신 스트림 데이터를 쿼리할 수 있음
- Amazon Redshift 스트리밍 수집은 스트림 소비자 역할을 수행

### Where
#### 스트리밍 수집 사용 사례
- 실시간에 가까운 분석: 지속적으로 생성(스트리밍)되고 짧은 생성 기간(지연 시간) 내에 처리되어야 하는 데이터 작업
- 데이터 소스는 다양할 수 있으며 IoT 디바이스, 시스템 원격 측정 데이터 또는 사용량이 많은 웹 사이트 또는 애플리케이션의 클릭스트림 데이터를 포함할 수 있음


## Amazon Redshift Spectrum
- Delta Lake에서 Amazon Redshift를 사용하여 Amazon S3 데이터 레이크의 테이블에 대해 읽기 쿼리를 실행할 수 있음
- Redshift Spectrum은 ETL을 수행하거나 데이터를 로드할 필요 없이 Redshift, 레이크 하우스, 운영 데이터베이스에서 데이터를 쿼리할 수 있는 레이크 하우스 아키텍처를 지원

## Amazon Redshift ML
- Amazon Redshift의 데이터로 기계학습 모델 생성 및 예측 가능<br>
    ㄴ 이전에는 Amazon Redshift에서 Amazon S3 버킷으로 훈련 데이터를 내보낸 다음, 기계학습 모델 훈련 과정을 구성하고 시작해야 했음 (예시: [Amazon SageMaker](https://aws.amazon.com/sagemaker/))

## Azure Synapse Analytics
Amazon Redshift에 대응되는 Microsoft Azure의 제품은 *Azure Synapse Analytics*
- Azure Synapse Analytics는 대규모 데이터 웨어하우징 및 빅데이터 분석 솔루션을 제공
- 사용자는 Petabyte 규모의 데이터에 대한 SQL 쿼리를 빠르게 실행할 수 있음
- 실시간 분석, 머신러닝, 데이터 탐색과 같은 다양한 기능을 통합하여 제공


## Reference
- [Amazon Redshift : 스트리밍 수집](https://docs.aws.amazon.com/ko_kr/redshift/latest/dg/materialized-view-streaming-ingestion.html)
- [Amazon Redshift ML 정식 출시 – SQL기반 기계 학습 모델 생성 및 예측 수행 (서울 리전 포함)](https://aws.amazon.com/ko/blogs/korea/amazon-redshift-ml-is-now-generally-available-use-sql-to-create-machine-learning-models-and-make-predictions-from-your-data/)