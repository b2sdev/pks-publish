
## 가격 대비 성능이 중요한 이유
- 사용자들은 지속적으로 생산되는 데이터를 분석하기 위해 더욱더 많은 데이터를 데이터 웨어하우스로 가져옴
- 데이터 웨어하우스에 데이터가 증가할수록 비용이 증가하는 반면 성능은 떨어지게 됨
- AWS에서는 가격 대비 성능의 비율을 지속적으로 개선하기 위한 활동을 전개하고 있음

## Amazon Redshift의 가격 대비 성능을 개선하기 위한 활동들

1. 낮은 지연시간과 높은 동시성 쿼리 성능 개선
    - 오늘날의 분석 애플리케이션 트렌드로 사용자들은 낮은 지연시간과 높은 동시성 쿼리를 요구

2. 진화하는 데이터 환경에 따른 새로운 기능들 추가 (추가 비용 없이 사용 가능)
    - 예: AWS Nitro System을 이용한 동급 대비 최고 하드웨어, AQUA를 이용한 하드웨어 가속, 구체화된 뷰(Materialized view)를 이용하여 더 빠른 실행을 위한 자동 재작성 쿼리(auto-rewriting query), 스키마 최적화를 위한 자동 테이블 최적화 작업(Automatic Table Optimization, ATO), 다이내믹한 동시성과 리소스 활용 최적화를 위한 자동 워크로드 관리(Automatic Workload Management, WLM), 단기 실행 쿼리 가속, 자동 구체화된 보기(Automatic materialized view), 벡터화 및 단일 명령 다중 데이터(single instruction/multiple data, SIMD) 처리와 같은 기능들

## 개선 활동의 결과
1. 분석 워크로드의 최적화를 통해 경쟁사 대비 최대 8배의 더 나은 성능을 제공
2. 성능 벤치마크를 실행하여 경쟁사 대비 최고의 가격 대비 성능을 제공하는 것을 확인함

## References
https://aws.amazon.com/ko/blogs/tech/amazon-redshift-continues-its-price-and-performance/
