---
id: yplkp47jvnjh21h7w1h4rev
title: 지수 평활법 (지수 이동 평균법)
desc: ''
updated: 1667828036672
created: 1667828036672
---

## 지수 평활법 (지수 이동 평균법, EMA, Exponential Moving Average)

- 과거 데이터 중 현재에 가까운 데이터에 보다 큰 비중을 주고 과거로 갈수록 웨이트가 적어지게(지수 함수적으로 감소)하는 방법
- 이동 평균법에 비해 현재의 상태가 직저ㄴ의 상태에 강한 영향을 받거나 상태의 변동에 가급적 추종하고 싶은 경우에 사용
- 단기적인 예측에 적합
- 재무상의 시계열 예측이나 주가 변동 분석 등에 사용
- 예측 값 = a x 전회 실적치 + (1 - a) x 전회 예측치 = 전회 예측치 + a x (전회 실적치 - 전회 예측치)
  - 전회 실적 값과 예측 값의 차이에 일정한 계수 a를 곱해서 생긴 추정치를 이전 예측치에 가감함으로써 이번 전망치를 산출
