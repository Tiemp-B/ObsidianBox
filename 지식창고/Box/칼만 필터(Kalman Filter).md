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
    x_pred = A*x_est + B*u  // u : 제어입력
                            // 등속 모델 시 A = 1, B = 0 
                            // 자연스러운 시스템 동역학 -> A*x_est
                            // 외부에서 의도적으로 가하는 조작/입력 -> B*u
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

다차원 버전
```
[표기]
x : 상태 벡터 (n x 1)
P : 오차 공분산 행렬 (n x n)
A : 상태 전이 행렬 (다음 상태 = A * 현재 상태)
B : 제어입력 행렬
u : 제어입력 벡터
Q : 프로세스 노이즈 공분산 (모델 불확실성)
H : 관측 모델 행렬 (상태 -> 측정값 매핑)
R : 측정 노이즈 공분산 (센서 불확실성)
z : 측정값 벡터

[초기화]
x = x0
P = P0

[매 스텝 반복]
1) 예측
    x_pred = A @ x + B @ u
    P_pred = A @ P @ A.T + Q
    
2) 보정
   y = z - H @ x_pred
   S = H @ P_pred @ H.T + R
   K = P_pred @ H.T @ inv(S)
   
    x = x_pred + K @ y
    P = (I - K @ H) @ P_pred       
```

<aside>C 구현 예시</aside>

스칼라(1차원) 버전
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

다차원(행렬형) 버전 — 등속 모델(상태 = 위치·속도)
```c
#include <string.h>

#define KF_N 2   // 상태 벡터 차원: [위치, 속도]
#define KF_M 1   // 측정 벡터 차원: [위치]
                 // (이 구현은 M <= N 을 가정)

typedef struct {
    float x[KF_N];          // 상태 추정 벡터        (N)
    float P[KF_N * KF_N];   // 오차 공분산 행렬       (N×N)
    float A[KF_N * KF_N];   // 상태 전이 행렬         (N×N)
    float H[KF_M * KF_N];   // 관측(측정) 행렬        (M×N)
    float Q[KF_N * KF_N];   // 프로세스 노이즈 공분산 (N×N)
    float R[KF_M * KF_M];   // 측정 노이즈 공분산     (M×M)
} KalmanND;

/* ---------- 작은 행렬 연산 헬퍼 (행 우선 저장) ---------- */

// out(ra×cb) = A(ra×ca) · B(ca×cb)
static void mat_mul(const float *A, const float *B, float *out,
                    int ra, int ca, int cb) {
    for (int i = 0; i < ra; i++)
        for (int j = 0; j < cb; j++) {
            float s = 0.0f;
            for (int k = 0; k < ca; k++) s += A[i*ca + k] * B[k*cb + j];
            out[i*cb + j] = s;
        }
}

// out(c×r) = A(r×c)^T
static void mat_trans(const float *A, float *out, int r, int c) {
    for (int i = 0; i < r; i++)
        for (int j = 0; j < c; j++)
            out[j*r + i] = A[i*c + j];
}

static void mat_add(const float *A, const float *B, float *out, int n) {
    for (int i = 0; i < n; i++) out[i] = A[i] + B[i];
}
static void mat_sub(const float *A, const float *B, float *out, int n) {
    for (int i = 0; i < n; i++) out[i] = A[i] - B[i];
}

// 가우스-조던 역행렬: out = inv(A), A는 n×n (작은 행렬 가정, n <= KF_N)
static int mat_inv(const float *A, float *out, int n) {
    float aug[KF_N][2 * KF_N];              // 확장 행렬 [A | I]
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++) {
            aug[i][j]     = A[i*n + j];
            aug[i][n + j] = (i == j) ? 1.0f : 0.0f;
        }
    for (int col = 0; col < n; col++) {
        float piv = aug[col][col];
        if (piv == 0.0f) return 0;          // 특이(비가역) 행렬
        for (int j = 0; j < 2*n; j++) aug[col][j] /= piv;
        for (int row = 0; row < n; row++) {
            if (row == col) continue;
            float f = aug[row][col];
            for (int j = 0; j < 2*n; j++) aug[row][j] -= f * aug[col][j];
        }
    }
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            out[i*n + j] = aug[i][n + j];
    return 1;
}

/* ---------- 예측 단계 ---------- */
void kf_predict(KalmanND *f) {
    float x_new[KF_N];
    float AP[KF_N*KF_N], At[KF_N*KF_N], APAt[KF_N*KF_N];

    // x = A · x
    mat_mul(f->A, f->x, x_new, KF_N, KF_N, 1);
    memcpy(f->x, x_new, sizeof x_new);

    // P = A · P · Aᵀ + Q
    mat_mul(f->A, f->P, AP, KF_N, KF_N, KF_N);
    mat_trans(f->A, At, KF_N, KF_N);
    mat_mul(AP, At, APAt, KF_N, KF_N, KF_N);
    mat_add(APAt, f->Q, f->P, KF_N*KF_N);
}

/* ---------- 보정 단계 (z: 측정 벡터 M×1) ---------- */
void kf_update(KalmanND *f, const float *z) {
    float Hx[KF_M], y[KF_M];
    float Ht[KF_N*KF_M], PHt[KF_N*KF_M];
    float HPHt[KF_M*KF_M], S[KF_M*KF_M], Sinv[KF_M*KF_M];
    float K[KF_N*KF_M], Ky[KF_N];
    float KH[KF_N*KF_N], I[KF_N*KF_N], ImKH[KF_N*KF_N], Pnew[KF_N*KF_N];

    // y = z - H · x   (잔차)
    mat_mul(f->H, f->x, Hx, KF_M, KF_N, 1);
    mat_sub(z, Hx, y, KF_M);

    // S = H · P · Hᵀ + R
    mat_trans(f->H, Ht, KF_M, KF_N);          // Ht: N×M
    mat_mul(f->P, Ht, PHt, KF_N, KF_N, KF_M);  // PHt: N×M
    mat_mul(f->H, PHt, HPHt, KF_M, KF_N, KF_M);// HPHt: M×M
    mat_add(HPHt, f->R, S, KF_M*KF_M);

    // K = P · Hᵀ · S⁻¹   (칼만 이득, N×M)
    mat_inv(S, Sinv, KF_M);
    mat_mul(PHt, Sinv, K, KF_N, KF_M, KF_M);

    // x = x + K · y
    mat_mul(K, y, Ky, KF_N, KF_M, 1);
    mat_add(f->x, Ky, f->x, KF_N);

    // P = (I - K · H) · P
    mat_mul(K, f->H, KH, KF_N, KF_M, KF_N);    // KH: N×N
    for (int i = 0; i < KF_N*KF_N; i++) I[i] = 0.0f;
    for (int i = 0; i < KF_N; i++) I[i*KF_N + i] = 1.0f;
    mat_sub(I, KH, ImKH, KF_N*KF_N);
    mat_mul(ImKH, f->P, Pnew, KF_N, KF_N, KF_N);
    memcpy(f->P, Pnew, sizeof Pnew);
}

/* ---------- 등속(constant-velocity) 모델 초기화 ---------- */
// dt: 시간 간격, q: 프로세스 노이즈, r: 측정 노이즈
void kf_init_cv(KalmanND *f, float dt, float q, float r) {
    float A[KF_N*KF_N] = { 1, dt,      // 위치 += 속도·dt
                           0, 1  };
    float H[KF_M*KF_N] = { 1, 0 };     // 위치만 측정
    float Q[KF_N*KF_N] = { q, 0,
                           0, q };
    float R[KF_M*KF_M] = { r };
    float P[KF_N*KF_N] = { 1, 0,
                           0, 1 };
    memcpy(f->A, A, sizeof A);
    memcpy(f->H, H, sizeof H);
    memcpy(f->Q, Q, sizeof Q);
    memcpy(f->R, R, sizeof R);
    memcpy(f->P, P, sizeof P);
    f->x[0] = 0.0f;   // 초기 위치
    f->x[1] = 0.0f;   // 초기 속도
}

/* 사용 예:
 *   KalmanND kf;
 *   kf_init_cv(&kf, 0.1f, 0.01f, 0.1f);
 *   float z[KF_M] = { measured_position };
 *   kf_predict(&kf);      // 예측
 *   kf_update(&kf, z);    // 보정
 *   // kf.x[0] = 추정 위치, kf.x[1] = 추정 속도
 */
```
스칼라 버전과 달리 상태를 벡터(위치·속도)로 두어, 위치만 측정해도 **속도까지 함께 추정**한다. 상태 전이 행렬 `A`가 "위치 += 속도·dt"라는 운동 모델을 담고, 관측 행렬 `H`가 상태 중 어떤 성분이 측정되는지를 정의한다. 스칼라의 나눗셈이 여기서는 행렬 역행렬(`inv(S)`)로 일반화되며, `KF_N`·`KF_M`과 `A`·`H`·`Q`·`R`만 바꾸면 더 높은 차원(예: 2D 위치+속도, IMU 융합)으로 확장할 수 있다.



---

<aside>핵심 정리</aside>

- 칼만 필터는 운동 모델 기반 예측과 센서 측정값을 확률적으로 결합해 상태를 추정하는 재귀적 필터다
- 측정값만 단순히 사용하는 것이 아니라, 예측-보정 사이클이 핵심이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 베이즈 필터와 칼만 필터]], [[4. 센서 데이터 융합(Sensor Fusion)]], [[6. 센서 피드백과 신호처리]], [[5. 데이터 로깅과 이상치 탐지]], [[2. 센서 성능 지표(분해능·IMU 드리프트)]]
- 관련: [[이동평균 필터(Moving Average Filter)]], [[센서 데이터 융합(Sensor Fusion)]], [[추측항법(Dead Reckoning)]], [[IMU(Inertial Measurement Unit)]], [[상보 필터(Complementary Filter)]]
