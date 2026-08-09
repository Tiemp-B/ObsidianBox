---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 신호처리
  - 필터
  - 위치추정
---

# Summary

칼만 필터는 시스템의 **운동 모델로 예측한 값과 센서의 실제 측정값을 확률적으로 결합**해, 각각 단독으로 쓰는 것보다 더 정확한 상태(위치·속도 등) 추정치를 계산하는 재귀적 필터다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>칼만 필터의 예측-보정 사이클</aside>

- 예측(Prediction) 단계: 이전 상태와 시스템의 운동 모델(예: "일정 속도로 움직인다")을 이용해 다음 상태를 미리 예측
- 보정(Update) 단계: 실제 센서 측정값이 들어오면, 예측값과 측정값을 각각의 **불확실성(신뢰도)에 따라 가중 평균**해 최종 추정치를 계산
- 예측과 측정 중 불확실성이 더 작은(더 신뢰할 수 있는) 쪽에 더 큰 가중치를 자동으로 부여함

"칼만 필터는 센서 측정값만을 그대로 사용하며, 시스템의 운동 모델에 기반한 예측 과정은 포함하지 않는다"라는 서술은 오답이다 — 칼만 필터의 핵심은 오히려 **운동 모델 기반 예측과 실제 측정값을 함께 결합**하는 것이며, 이 예측-보정 사이클이 이동평균 필터 같은 단순 필터와의 결정적 차이다.

<aside>이동평균 필터와의 선택 기준</aside>

단순히 잡음만 완화하면 되는 상황은 [[이동평균 필터(Moving Average Filter)]]로 충분하지만, 시스템의 운동을 예측하며 여러 센서를 정밀하게 융합해야 하는 상황(위치 추정, IMU 융합 등)은 칼만 필터가 더 적합하다.

<aside>의사코드</aside>

스칼라 버전
```
[Initial]
x_est = 초기 추정값  // 상태 추정치
P = 초기 오차 공분산 // 추정 오차의 불확실성

[Repeat on Step]
1) Predict
    x_pred = A*x_est + B*u  // 등속 모델 시 A = 1, B = 0
    P_pred = P + Q          // 불확실성 증가 Q : 프로세스 노이즈
    
2) Update
    K = P_pred / (P_pred + R)  // 칼만 이득 계산 (R: 측정 노이즈)
    
    x_est = x_pred + K * (z - x_pred)  // z : 새 측정값, (z - x_pred) : 잔차
    P = (1 - K) * P_pred // 불확실성 감소
   
FUNCTION KalmanUpdate(measurement):
    // 1) 예측 단계
    p = p + q

    // 2) 보정 단계
    k = p / (p + r)
    x = x + k * (measurement - x)
    p = (1 - k) * p

    RETURN x
```

<aside>C 구현 예시</aside>

```c
typedef struct {
    float x;      // 상태 추정값(예: 위치)
    float p;      // 추정 오차 공분산
    float q;      // 프로세스 노이즈(모델 불확실성)
    float r;      // 측정 노이즈(센서 불확실성)
    float k;      // 칼만 이득
} KalmanFilter1D;

void kf_init(KalmanFilter1D *f, float initial_x, float q, float r) {
    f->x = initial_x;
    f->p = 1.0f;
    f->q = q;
    f->r = r;
}

float kf_update(KalmanFilter1D *f, float measurement) {
    // 1) 예측(Prediction) 단계 — 등속 모델 가정, 별도 입력 없으면 x, p만 갱신
    f->p = f->p + f->q;

    // 2) 보정(Update) 단계
    f->k = f->p / (f->p + f->r);                 // 칼만 이득
    f->x = f->x + f->k * (measurement - f->x);    // 예측값과 측정값을 가중 결합
    f->p = (1.0f - f->k) * f->p;                  // 오차 공분산 갱신

    return f->x;
}
```
가장 단순한 스칼라(1차원) 칼만 필터 예시로, `q`(모델 신뢰도)와 `r`(센서 신뢰도)의 상대적 크기에 따라 칼만 이득 `k`가 자동으로 예측값·측정값 중 더 신뢰할 쪽에 가중치를 싣는다.

---

<aside>핵심 정리</aside>

- 칼만 필터는 운동 모델 기반 예측과 센서 측정값을 확률적으로 결합해 상태를 추정하는 재귀적 필터다
- 측정값만 단순히 사용하는 것이 아니라, 예측-보정 사이클이 핵심이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 베이즈 필터와 칼만 필터]], [[4. 센서 데이터 융합(Sensor Fusion)]], [[6. 센서 피드백과 신호처리]], [[5. 데이터 로깅과 이상치 탐지]], [[2. 센서 성능 지표(분해능·IMU 드리프트)]]
- 관련: [[이동평균 필터(Moving Average Filter)]], [[센서 데이터 융합(Sensor Fusion)]], [[추측항법(Dead Reckoning)]], [[IMU(Inertial Measurement Unit)]], [[상보 필터(Complementary Filter)]]
