---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 신호처리
  - 필터
---

# Summary

저역통과 필터(Low-pass Filter)는 신호에서 **낮은 주파수 성분은 통과시키고, 높은 주파수 성분(고주파 잡음)은 감쇠**시키는 필터로, 센서 신호에 섞인 순간적인 노이즈를 제거하는 데 널리 쓰인다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>저역통과 필터의 원리</aside>

- 센서 노이즈는 흔히 신호가 급격히 튀는 형태(고주파 성분)로 나타나는 반면, 실제 물리량의 변화는 대체로 완만함(저주파 성분)
- 저역통과 필터는 이 저주파 성분(실제 신호)은 그대로 두고, 고주파 성분(노이즈)만 걸러내 **매끄러운 신호**를 얻음
- 과거로 갈수록 가중치가 줄어드는 가중 평균. 평균화되는 과정에서 각 값에 있는 고주파 잡음이 서로 상쇄되어 사라진다.
- 차단 주파수(cutoff frequency)를 낮게 설정할수록 더 많은 고주파 성분을 걸러내지만, 실제 신호의 빠른 변화까지 둔감하게 만들 위험도 커짐(지연 증가)

<aside>시간영역 관점</aside>

```
새 출력 값 = 새 측정값(x[n])과 직전 출력값(y[n-1])의 가중평균
y[n] = α · x[n] + (1-α) · y[n-1]

재귀적 수식
y[n] = α·x[n] + α(1-α)·x[n-1] + α(1-α)²·x[n-2] + α(1-α)³·x[n-3] + ...
```
과거로 갈수록 가중치가 지수적으로 줄어드는 가중 평균

<aside>주파수영역 관점</aside>

```
라플라스/Z변환 분석
H(z) = α / (1 - (1-α)z⁻¹)

gain 식
|H(ω)| = α / √(1 - 2(1-α)cos(ω) + (1-α)²)
```

- ω = 0 (직류/저주파)일 때: `|H(0)| = 1` → 그대로 통과
- ω가 커질수록(고주파): 분모가 커지면서 `|H(ω)|`가 점점 작아짐 → **감쇠**
- ω = π (나이퀴스트, 최고 주파수, 즉 매 샘플마다 부호가 뒤집히는 잡음)일 때 감쇠가 가장 큼

<aside>트레이드오프</aside>

α 값이 작으면 신호 변화를 늦게 따라가며, 너무 크면 노이즈 감쇠 효과가 줄어든다
α는 차단 주파수를 직접 결정하는 파라미터이며 관계식은 대략 다음과 같다.

$$ \alpha \approx 2\pi \cdot f_c \cdot T_s $$

실제 신호의 변화 속도(대역폭)보다 약간 위, 잡음 주파수보다는 훨씬 아래로 차단주파수를 지정하여 α를 역산한다

<aside>의사코드</aside>

```
FUNCTION LowPassFilter(new_sample, alpha, prev_output):
    output = alpha * new_sample + (1 - alpha) * prev_output
    RETURN output
```

<aside>C 구현 예시</aside>

```c
typedef struct {
    float alpha;      // 0~1, 클수록 최신 값 반영 비중이 큼(=필터링 약함)
    float prev_output;
    int initialized;
} LowPassFilter;

void lpf_init(LowPassFilter *f, float alpha) {
    f->alpha = alpha;
    f->initialized = 0;
}

float lpf_update(LowPassFilter *f, float new_sample) {
    if (!f->initialized) {
        f->prev_output = new_sample;
        f->initialized = 1;
        return new_sample;
    }
    // y[n] = alpha * x[n] + (1 - alpha) * y[n-1]
    f->prev_output = f->alpha * new_sample + (1.0f - f->alpha) * f->prev_output;
    return f->prev_output;
}
```
가장 흔히 쓰이는 1차 IIR(지수가중이동평균) 형태로, alpha가 작을수록 노이즈 제거는 강해지지만 지연도 커진다.

---

<aside>핵심 정리</aside>

- 저역통과 필터는 저주파 성분은 통과시키고 고주파 성분(노이즈)을 걸러내는 필터다
- 고주파를 통과시키고 저주파를 거르는 것이 아니라, 그 반대다

---

<aside>관련 노트</aside>

- 원 페이지: [[6. 센서 피드백과 신호처리]]
- 관련: [[이동평균 필터(Moving Average Filter)]]
