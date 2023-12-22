
## 이벤트 기반 아키텍처

이벤트 스트림을 생성하는 이벤트 생산자와 이벤트를 수신 대기하는 이벤트 소비자로 구성됨

![Alt](https://learn.microsoft.com/ko-kr/azure/architecture/guide/architecture-styles/images/event-driven.svg)

### 모델
- 게시자/구독자 모델 : 이벤트가 게시되면 각 구독자에게 이벤트를 보냄, 이벤트를 받은 후에는 재생 불가
- 이벤트 스트리밍 : 이벤트가 로그에 저장되며, 클라이언트는 스트림을 재생하는 방식으로 읽음

### 처리 방식
- 단순 이벤트 처리 : 이벤트가 즉시 소비자에서 작업을 트리거 (예: Azure Service Bus에 메시지가 게시되면 Azure Functions가 실행)
- 복잡한 이벤트 처리 : 이벤트 데이터에서 패턴을 찾으면서 일련의 이벤트를 처리 (예: 디바이스에서 일정 기간 동안 읽은 값을 집계하여 이동 평균이 특정 임계값을 초과하면 알림 생성)
- 이벤트 스트림 처리 : 데이터 스트리밍 플랫픔을 사용하여 이벤트를 수집하고 스트림 프로세서에 공급

### 이점
- 생산자와 소비자가 분리됨
- 시스템에 새 소비자를 쉽게 추가할 수 있음
- 이벤트가 도착하는 즉시 소비자가 이벤트에 응답할 수 있음
- 확장성이 뒤어남

## References
- https://learn.microsoft.com/ko-kr/azure/architecture/guide/architecture-styles/event-driven