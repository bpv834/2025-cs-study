<img width="665" height="336" alt="image" src="https://github.com/user-attachments/assets/95fbcf3a-52c4-4bdd-a1ca-0d5dc9d07495" /># Graph

## 그래프의 종류와 개념

#### 그래프는 여러 개의 점(**노드** 또는 **정점**)들이 선(**간선**)으로 연결된 구조를 나타내는 **수학적인 개념**입니다.

---

### 그래프의 용어

<img width="571" height="316" alt="image" src="https://github.com/user-attachments/assets/3b6d19ac-5894-47cc-b063-331940f54ba3" />

---

### 🟢 노드(Node) 또는 정점(Vertex)
그래프에서 **하나의 점**을 나타냅니다.  
노드는 데이터를 저장하거나, 특정 객체를 표현하는 데 사용됩니다.

---

### 🟣 간선(Edge)
그래프에서 **노드와 노드를 연결하는 선**을 의미합니다.  
간선은 두 노드 간의 **관계(Relationship)** 또는 **연결(Connection)** 을 표현합니다.

---

### 🟠 인접(Adjacent)
두 개의 노드가 **간선으로 직접 연결되어 있는 상태**를 말합니다.  
인접한 노드는 서로 **이웃 노드(Neighbor)** 라고도 부릅니다.

---

### 🔵 차수(Degree)
특정 노드에 **연결된 간선의 개수**를 의미합니다.  
- **무방향 그래프(Undirected Graph)**:  
  → 해당 노드와 인접한 노드의 수 = 차수  
- **방향 그래프(Directed Graph)**:  
  → 들어오는 간선(In-degree)과 나가는 간선(Out-degree)으로 구분됩니다.
  
  → 총 차수 = 진입 차수 + 진출 차수

---

### 🟡 경로(Path)
그래프에서 **노드들을 연결하는 간선의 순서**를 말합니다.  
- 경로의 **길이** = 경로에 포함된 **간선의 수**  
- 예시: `A → B → C → D` (경로의 길이 = 3)

---

### 🔴 사이클(Cycle)
그래프 내에서 **같은 노드로 되돌아오는 경로**를 의미합니다.  
즉, **경로의 시작 노드와 끝 노드가 동일한 경우**를 말합니다.  
- 예시: `A → B → C → A`

---

### ⚫ 가중치(Weight)
**가중치 그래프(Weighted Graph)** 에서 간선에 부여된 **값 또는 비용**을 의미합니다.  
가중치는 이동 거리, 시간, 비용 등의 **간선의 특성**을 표현할 수 있습니다.  
- 예시:  
  - 도로 거리 그래프 → 거리(km)  
  - 네트워크 그래프 → 전송 시간(ms)

---
## 그래프의 종류

#### 무방향 그래프 & 방향 그래프
- 간선의 방향의 유무에 따라 구분되는 그래프

<img width="539" height="308" alt="image" src="https://github.com/user-attachments/assets/b045d35c-329a-4601-8450-d175841c879a" />

#### 가중치 그래프
- 그래프에 가중치 또는 비용이 할당된 그래프(네트워크 이론이나 신경망 이론에 활용되는 개념)
<img width="752" height="357" alt="image" src="https://github.com/user-attachments/assets/d3844d2d-5716-422d-babb-de419ce9d8c0" />

#### 연결 그래프 & 비연결 그래프
-  모든 노드에 대해 경로가 존재하면 연결 그래프, 특정 노드에 대한 경로가 하나라도 존재하지 않을 경우 비연결 그래프
<img width="689" height="346" alt="image" src="https://github.com/user-attachments/assets/b5c4175e-f280-44dd-b0fa-6dd2ce0be7ca" />

#### 사이클 그래프 & 비순환 그래프
<img width="688" height="333" alt="image" src="https://github.com/user-attachments/assets/a66b544d-0070-4c47-8535-863e97c5f9ff" />

#### 완전 그래프
-  그래프의 모든 노드가 연결되어 있는 그래프
  <img width="665" height="336" alt="image" src="https://github.com/user-attachments/assets/0efce944-d816-4099-9bff-959e45f81559" />


## 그래프를 나타내기 위한 자료 구조

---

### 1️⃣ 인접 행렬 (Adjacency Matrix)

그래프를 **2차원 배열(Matrix)** 로 표현하는 방식입니다.  
노드의 개수를 `N`이라 할 때, `N x N` 크기의 행렬을 사용하여  
각 노드 간의 **연결 관계(간선 존재 여부)** 를 나타냅니다.

#### 🧩 예시

<img width="715" height="311" alt="image" src="https://github.com/user-attachments/assets/ebc0d849-47e5-42bf-a534-6519dc83d47c" />

---

#### ✅ 장점
- **인접한 노드의 존재 여부**를 쉽게 확인할 수 있음  
- **간선의 존재 여부를 O(1)** 시간에 확인 가능  


#### ⚠️ 단점
- **노드 수가 많고 간선이 적은 희소 그래프(Sparse Graph)** 에서 **메모리 낭비가 큼**  
- **O(V²)** 의 공간이 필요하므로 **공간 효율성이 낮음**


📘 **요약**
> 인접 행렬은 **간선 확인은 빠르지만**,  
> **공간 효율성이 떨어지는 그래프 표현 방식**이다.

---

### 2️⃣ 인접 리스트 (Adjacency List)

그래프를 **각 노드마다 인접한 노드들의 리스트**로 표현하는 방식입니다.  
노드의 개수를 `N`이라 할 때, **N개의 리스트(List)** 를 사용하여  
각 노드와 **직접 연결된 노드들**을 저장합니다.

#### 🧩 예시
- 방향

<img width="605" height="311" alt="image" src="https://github.com/user-attachments/assets/d2b98ad4-50d3-4939-9f7d-f5e519327cb3" />


- 무방향

<img width="830" height="311" alt="image" src="https://github.com/user-attachments/assets/fe420194-fd2e-45d4-9955-e6a9c7bc9d27" />


