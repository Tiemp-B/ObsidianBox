---
cssclasses: cornell-note
tags:
---
<div class="cues-header">Cues</div>

# Summary
<summary>최소 신장 트리(Minimum Spanning Tree, MST)의 개념과 대표 알고리즘 및 Union-Find의 역할을 정리한다.</summary>
가중 그래프에서 모든 정점을 최소 비용으로 연결하는 트리를 찾는 과정과, 이를 구현하는 Kruskal 알고리즘 및 Union-Find 자료구조의 연관성을 다룸.

---

# Notes

<aside>정의</aside>
MST(Minimum Spanning Tree)는 **가중치가 있는 연결 그래프**에서
모든 정점을 **최소 비용으로 연결하는 부분 그래프**를 의미한다.
트리는 사이클이 없으며, 모든 정점을 포함하고, 간선의 총 가중치가 최소가 된다.
즉, 연결성과 최소비용을 동시에 만족시키는 구조이다.

---

<aside>알고리즘 종류</aside>
1. **Kruskal 알고리즘**
   - 간선을 가중치 기준으로 정렬한 뒤, 사이클이 생기지 않도록 작은 간선부터 선택.
   - **Union-Find(Disjoint Set)** 자료구조를 이용해 정점 간 연결 여부를 추적하고, 사이클을 방지.
   - 절차:
     1. 간선을 가중치 오름차순으로 정렬.
     2. 각 간선의 양 끝 정점이 다른 집합에 속하면 해당 간선을 선택(Union 수행).
     3. 모든 정점이 연결될 때까지 반복.
   - 시간 복잡도: `O(E log E)` (정렬 + Union-Find 연산)

2. **Prim 알고리즘**
   - 임의의 정점에서 시작해, 방문하지 않은 정점 중 최소 가중치 간선을 선택하며 확장.
   - **우선순위 큐(Heap)** 사용 시 효율적.
   - 시간 복잡도: `O(E log V)`

---

<aside>Union-Find 구조</aside>
Union-Find는 Kruskal에서 **사이클 탐지 및 집합 병합**을 빠르게 수행하는 핵심 구조다.  
- **find(x)**: 원소 x가 속한 집합의 루트 노드를 찾는다.  
- **union(a, b)**: 두 원소가 속한 집합을 하나로 합친다.  
- **path compression**과 **union by rank/size** 기법을 통해 시간 복잡도를 거의 상수로 줄인다.  
- 전체 복잡도: `O(α(V))`, α는 아커만(Ackermann) 역함수로 매우 작음.

---

<aside>활용</aside>
- 통신망, 전력망, 도로망 등 **네트워크 구축 비용 최소화** 문제에 사용.
- **클러스터링(Cluster Analysis)**에서 그룹 간 거리 최소화를 위해 활용.
- **그래프 기반 경로 최적화**나 **지도 생성 알고리즘**의 기초로 사용됨.
