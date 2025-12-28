---
cssclasses: cornell-note
tags:
  - control
  - pid
  - control-theory
  - automation
  - engineering
---

# Summary

PID 제어는 목표값(Setpoint)과 실제 출력값의 오차를 기반으로  
비례(P), 적분(I), 미분(D) 요소를 결합해 시스템을 안정적으로 제어하는 방법이다.  
산업 자동화, 로봇, 모터 제어, 공정 제어 등에서 가장 널리 사용되는 고전 제어 기법이다.
![[Pasted image 20251228200157.png]]

---

<div class="cues-header">Cues</div>

# Notes

<aside>PID 제어 개요</aside>

PID 제어는 피드백 제어 방식의 대표적인 기법으로,  
현재 오차, 누적 오차, 오차 변화율을 동시에 고려해 제어 입력을 결정한다.

$$
u(t) = {K_p}e(t)+{K_i}\int_{0^t}e(\tau)d\tau+K_{d}\frac{de}{dt}
$$


제어 목적:  
- 목표값에 빠르게 도달  
- 진동 최소화  
- 안정 상태 오차 제거  

구조가 단순하면서도 실용성이 매우 높아 산업 표준으로 사용된다.

---

<aside>비례 제어 (P: Proportional)</aside>

비례 제어는 **현재 오차 크기에 비례**하여 제어량을 조절한다.

$$
K_pe(t)
$$
K는 게인

특징:  
- 반응 속도 빠름  
- 오차가 클수록 큰 제어 입력  
- 단독 사용 시 정상 상태 오차(Steady-state error) 발생 가능  

과도하게 크면 진동이나 오버슈트 발생 위험이 있다.

---

<aside>적분 제어 (I: Integral)</aside>

적분 제어는 **과거 오차의 누적값**을 기반으로 제어한다.

특징:  
- 정상 상태 오차 제거  
- 장기적인 편차 보정  
- 응답 속도 저하 가능  
- 적분 포화(Integral Windup) 문제 발생 가능  

P 제어의 한계를 보완하지만, 단독 사용은 불안정하다.

---

<aside>미분 제어 (D: Derivative)</aside>

미분 제어는 **오차의 변화율**을 기준으로 제어한다.

특징:  
- 미래 오차를 예측하는 효과  
- 오버슈트 감소  
- 시스템 안정성 향상  
- 노이즈에 민감  

주로 진동 억제와 응답 안정화에 사용된다.

---

<aside>PID 결합 제어</aside>

PID 제어는 P, I, D를 조합해 각 요소의 단점을 상호 보완한다.

- P: 빠른 반응  
- I: 오차 제거  
- D: 안정성 강화  

이 조합으로  
빠르고 정확하며 안정적인 제어 성능을 달성할 수 있다.

---

<aside>PID 튜닝</aside>

PID 제어의 성능은 계수(Kp, Ki, Kd) 설정에 크게 의존한다.

대표적인 튜닝 방법:  
- 경험적 튜닝(Manual Tuning)  
- Ziegler–Nichols 방법  
- Cohen–Coon 방법  
- 자동 튜닝(Auto-tuning)  

튜닝 목표는 응답 속도, 안정성, 오버슈트 간 균형이다.

---

<aside>적용 분야</aside>

- 모터 속도·위치 제어  
- 로봇 관절 제어  
- 온도·압력·유량 제어  
- 공정 자동화(반도체, 화학, 제조)  
- 드론·자율주행 제어 시스템  

임베디드 시스템과 산업 제어 전반에 광범위하게 적용된다.

---

<aside>한계와 확장</aside>

PID 제어의 한계:  
- 비선형 시스템 대응 한계  
- 지연(Time Delay)에 취약  
- 복잡한 다변수 시스템 제어 어려움  

이를 보완하기 위해  
- Gain Scheduling  
- Adaptive Control  
- Model Predictive Control(MPC)  
등 고급 제어 기법이 사용된다.

---

<aside>핵심 정리</aside>

- PID 제어는 가장 널리 사용되는 피드백 제어 기법  
- P·I·D 요소가 각각 반응성, 정확성, 안정성을 담당  
- 튜닝이 성능의 핵심 요소  
- 산업 자동화·로봇·임베디드 제어의 기본 이론이다
