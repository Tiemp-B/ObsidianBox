---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 경로계획소프트웨어개발
---

# Summary

Pure Pursuit은 로봇 전방의 경로 위에 **목표점(look-ahead point)을 하나 정하고, 현재 위치에서 그 점으로 향하는 원호를 따라가도록 조향각을 계산**하는 단순하고 직관적인 경로 추종(path tracking) 알고리즘이다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Pure Pursuit의 동작 원리</aside>

- 경로 위에서 로봇 현재 위치로부터 일정 거리(look-ahead distance)만큼 앞선 지점을 목표점으로 선택
- 현재 위치·방향에서 그 목표점을 지나는 원호를 기하학적으로 계산하고, 그 원호를 따라가는 데 필요한 조향각(곡률)을 구함
- look-ahead distance가 짧으면 경로를 더 정밀하게 따라가지만 진동이 생기기 쉽고, 길면 부드럽지만 코너에서 경로를 크게 벗어날 수 있음

"Pure Pursuit은 look-ahead distance와 무관하게 항상 동일한 정확도로 경로를 추종하는 알고리즘이다"라는 서술은 오답이다 — Pure Pursuit의 추종 정확도와 부드러움은 오히려 **look-ahead distance 설정값에 따라 트레이드오프**가 발생하며, 이 값이 성능을 좌우하는 핵심 파라미터다.

<aside>DWA와의 관계</aside>

Pure Pursuit은 이미 정해진 전역 경로를 얼마나 잘 따라가는가(경로 추종)에 초점을 둔 반면, [[Dynamic Window Approach(DWA)]]는 장애물을 실시간으로 피하며 속도 자체를 새로 선택하는 데 초점을 둔다 — 실제로는 두 알고리즘을 상황에 따라 조합해 쓰기도 한다.

---

<aside>핵심 정리</aside>

- Pure Pursuit은 전방의 목표점을 향한 원호를 계산해 경로를 추종하는 알고리즘이다
- look-ahead distance 설정에 따라 정밀도와 부드러움 사이의 트레이드오프가 발생한다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. Pure Pursuit 경로 추종]]
- 관련: [[Dynamic Window Approach(DWA)]]
