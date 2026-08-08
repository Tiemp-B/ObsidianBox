---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 신호처리
  - 필터
---

# Summary

이동평균 필터는 최근 N개의 측정값을 **평균 내어 그 결과를 현재값으로 사용**하는 단순한 잡음 제거 필터로, 예측 모델 없이도 순간적인 잡음(노이즈)을 완화할 수 있다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>이동평균 필터의 동작과 한계</aside>

- 매 시점마다 최근 N개 샘플의 평균을 계산해 출력함 — N이 클수록 잡음은 더 매끄러워지지만, 실제 값 변화에 대한 반응도 그만큼 느려짐(지연 증가)
- 시스템의 동역학 모델이나 예측 없이, 단순히 과거 값들의 평균만 이용하는 **가장 단순한 형태의 잡음 완화 기법**
- [[칼만 필터(Kalman Filter)]]처럼 시스템 모델을 반영해 정밀하게 예측·추정하는 방식이 아니라, 계산이 훨씬 간단하고 직관적임

"이동평균 필터는 시스템의 운동 모델을 반영해 다음 상태를 예측하고, 예측값과 측정값을 확률적으로 결합하는 필터다"라는 서술은 오답이다 — 그것은 [[칼만 필터(Kalman Filter)]]의 특징이며, 이동평균 필터의 핵심은 오히려 **모델 없이 최근 값들을 단순 평균**한다는 점이다.

<aside>칼만 필터와의 선택 기준</aside>

단순히 잡음을 완화하는 목적이면 계산이 간단한 이동평균 필터로 충분하지만, 시스템의 운동을 예측하며 정밀한 상태 추정이 필요하면(예: 위치·속도 동시 추정) 칼만 필터가 더 적합하다 — 이 선택 기준이 두 필터를 구분하는 핵심 포인트다.

<aside>의사코드</aside>

```
FUNCTION MovingAverage(new_sample):
    buffer[index] = new_sample
    index = (index + 1) mod WINDOW_SIZE
    IF count < WINDOW_SIZE:
        count = count + 1
    average = SUM(buffer[0 .. count-1]) / count
    RETURN average
```

<aside>C 구현 예시</aside>

```c
#define WINDOW_SIZE 5

typedef struct {
    float buffer[WINDOW_SIZE];
    int index;
    int count;
    float sum;
} MovingAverageFilter;

void ma_init(MovingAverageFilter *f) {
    f->index = 0;
    f->count = 0;
    f->sum = 0.0f;
}

float ma_update(MovingAverageFilter *f, float new_sample) {
    if (f->count == WINDOW_SIZE) {
        f->sum -= f->buffer[f->index];   // 가장 오래된 값 제거
    } else {
        f->count++;
    }
    f->buffer[f->index] = new_sample;
    f->sum += new_sample;
    f->index = (f->index + 1) % WINDOW_SIZE;

    return f->sum / f->count;             // 현재 윈도우 평균
}
```
원형 버퍼(circular buffer)로 최근 N개 값만 유지하며, 매 호출마다 합계를 갱신해 O(1)로 평균을 계산한다.

---

<aside>핵심 정리</aside>

- 이동평균 필터는 최근 N개 값의 평균으로 잡음을 완화하는 단순한 필터다
- 시스템 모델 기반 예측이 없다는 점에서 칼만 필터와 다르며, 단순 잡음 완화에는 충분하지만 정밀 추정에는 한계가 있다

---

<aside>관련 노트</aside>

- 원 페이지: [[6. 센서 피드백과 신호처리]], [[5. 데이터 로깅과 이상치 탐지]]
- 관련: [[칼만 필터(Kalman Filter)]], [[저역통과 필터(Low-pass Filter)]]
