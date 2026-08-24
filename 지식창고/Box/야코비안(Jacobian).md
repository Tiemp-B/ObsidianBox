---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 경로계획소프트웨어개발
---

# Summary

야코비안 행렬은 로봇의 **관절 속도와 엔드이펙터 속도 사이의 선형 관계**($\dot x = J \dot q$)를 나타내는 행렬이며, 이 행렬이 랭크를 잃는(특이해지는) 자세가 곧 특이점(Singularity)이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>야코비안의 정의</aside>

야코비안 행렬 J는 관절 속도 벡터 $\dot q$를 엔드이펙터 속도 벡터 $\dot x$로 변환한다: $\dot x = J\dot q$. 순기구학 자체는 관절각과 위치의 **비선형** 관계이지만, 이를 미분한 속도 관계(야코비안)는 항상 **선형**이다.

<aside>야코비안 계산 방법 — 기하학적 야코비안(Geometric Jacobian)</aside>

각 열은 관절 $i$의 속도 1단위가 엔드이펙터의 선속도·각속도에 주는 영향을 나타내며, 순기구학에서 이미 구한 누적 변환행렬 $T_0^{i-1}=T_1T_2\cdots T_{i-1}$에서 **$z_{i-1}$**(관절 $i$의 회전축 방향, $T_0^{i-1}$ 회전 부분의 3번째 열)과 **$p_{i-1}$**(관절 $i$ 원점, $T_0^{i-1}$의 위치 부분)을 그대로 가져와 구성한다. 엔드이펙터 위치 $p_n$은 전체 $T=T_1T_2\cdots T_n$의 위치 부분이다.

관절 $i$가 **회전 관절**이면 $J_i=\begin{bmatrix}z_{i-1}\times(p_n-p_{i-1})\\z_{i-1}\end{bmatrix}$, **직동 관절**이면 $J_i=\begin{bmatrix}z_{i-1}\\0\end{bmatrix}$이다. 이 열들을 모아 $J=[J_1\ J_2\ \cdots\ J_n]$을 구성하면 위 3개 행은 선속도($\dot p$), 아래 3개 행은 각속도($\omega$)에 대응하는 $6\times n$ 행렬이 된다.

**검산 — 2자유도 평면 팔**: [[2. 순기구학 계산과 특이점]]에서 구한 $x=L_1\cos\theta_1+L_2\cos(\theta_1{+}\theta_2),\ y=L_1\sin\theta_1+L_2\sin(\theta_1{+}\theta_2)$을 각 관절각으로 직접 미분(해석적 야코비안)해도 위치 부분은 같은 결과가 나온다.

$$J=\begin{bmatrix}\dfrac{\partial x}{\partial\theta_1}&\dfrac{\partial x}{\partial\theta_2}\\\dfrac{\partial y}{\partial\theta_1}&\dfrac{\partial y}{\partial\theta_2}\end{bmatrix}=\begin{bmatrix}-L_1\sin\theta_1-L_2\sin(\theta_1{+}\theta_2)&-L_2\sin(\theta_1{+}\theta_2)\\L_1\cos\theta_1+L_2\cos(\theta_1{+}\theta_2)&L_2\cos(\theta_1{+}\theta_2)\end{bmatrix}$$

기하학적 야코비안과 해석적 야코비안은 선속도 열에서는 같은 결과를 주지만(둘 다 위치를 관절각으로 편미분), 자세(각속도) 성분의 표현 방식이 다르다 — 기하학적 야코비안은 실제 각속도 벡터 $\omega$를, 해석적 야코비안은 오일러각 등 자세 표현의 변화율을 쓴다.

<aside>야코비안과 특이점의 관계</aside>

야코비안의 열벡터들이 서로 독립이면(랭크가 가득 차면) 관절 속도의 조합으로 엔드이펙터를 어떤 방향으로도 움직일 수 있다. 하지만 특정 자세에서 야코비안이 **랭크를 잃으면(특이해지면)**, 그 방향으로는 엔드이펙터를 움직일 수 없거나 해당 방향으로 움직이려면 관절 속도가 무한대에 가까워진다 — 이 자세를 특이점이라 한다.

---

<aside>핵심 정리</aside>

- 야코비안은 관절 속도를 엔드이펙터 속도로 변환하는 행렬이다($\dot x = J\dot q$)
- 기하학적 야코비안은 각 열을 $z_{i-1}\times(p_n-p_{i-1})$(회전) 또는 $z_{i-1}$(직동)으로 구성하며, 순기구학에서 구한 누적 변환행렬의 $z_{i-1},p_{i-1}$을 그대로 재사용한다
- 야코비안이 랭크를 잃는 자세가 특이점이며, 이때 특정 방향의 움직임이 불가능해지거나 관절 속도가 비정상적으로 커진다

---

<aside>관련 노트</aside>

- 원 페이지: [[2. 순기구학 계산과 특이점]]
