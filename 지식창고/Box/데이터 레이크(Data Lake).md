---
cssclasses: cornell-note
tags:
  - 로봇소프트웨어개발기사
  - 로봇훈련
---

# Summary

데이터 레이크는 정형·비정형을 가리지 않고 데이터를 **가공 전 원본 그대로** 저장해 두는 저장소로, 스키마를 미리 정해 저장하는 [[데이터 웨어하우스(Data Warehouse)|데이터 웨어하우스]]와 저장 시점의 접근 방식이 반대다.

---

<div class="cues-header">Cues</div>

# Notes

<aside>Schema-on-Write vs Schema-on-Read</aside>

| 구분 | 데이터 웨어하우스 | 데이터 레이크 |
|---|---|---|
| 스키마 적용 시점 | 저장 전에 미리 정함(Schema-on-Write) | 조회할 때 필요한 대로 적용(Schema-on-Read) |
| 저장 형태 | [[ETL(Extract Transform Load)]]을 거친 정제된 구조적 데이터 | 원본(raw) 그대로, 정형·비정형 모두 |
| 장점 | 정해진 구조라 조회·분석이 빠르고 일관적 | 저장이 유연하고, 나중에 다양한 방식으로 재해석 가능 |

<aside>로봇 데이터에서의 활용</aside>

로봇의 원본 센서 로그·카메라 이미지처럼 나중에 어떤 형태로 쓰일지 아직 정해지지 않은 데이터를 우선 원본 그대로 데이터 레이크에 쌓아 두고, 이후 필요에 따라 가공해 데이터 웨어하우스로 옮기거나 직접 분석에 활용할 수 있다.

---

<aside>핵심 정리</aside>

- 데이터 레이크는 원본 데이터를 Schema-on-Read 방식으로 저장하며, Schema-on-Write인 데이터 웨어하우스와 스키마 적용 시점이 반대다
- 정제 전 원본을 유연하게 저장해 두었다가 필요할 때 구조를 적용하는 것이 핵심이다

---

<aside>관련 노트</aside>

- 원 페이지: [[3. 데이터 웨어하우스와 ETL]]
- 관련: [[데이터 웨어하우스(Data Warehouse)]], [[ETL(Extract Transform Load)]]
