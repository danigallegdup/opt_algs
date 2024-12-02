### Full Summary of Solutions for Problem Set 2

---

#### **Problem 1: Travelling Salesman and Independent Set**
---

##### **1.a. TSP Algorithm in \( O(2^n \cdot n^3) \)**
- **Objective**: Solve the Traveling Salesman Problem (TSP) using dynamic programming.
- **Approach**:
  1. Use a **bitmask DP** representation for subsets of cities.
     - Define \( dp[S][v] \): Minimum cost to visit all cities in \( S \) and end at city \( v \).
  2. Base Case:
     - \( dp[\{0\}][0] = 0 \), where \( 0 \) is the starting city.
  3. Transition:
     - For every subset \( S \) containing \( v \) and for every \( u \in S \setminus \{v\} \):
       \[
       dp[S][v] = \min_{u \in S, u \neq v} \{dp[S \setminus \{v\}][u] + dist(u, v)\}.
       \]
  4. Final Step:
     - \( \text{Result} = \min_{v \in V} \{dp[\{1, \dots, n\}][v] + dist(v, 0)\} \).
- **Time Complexity**: \( O(2^n \cdot n^2) \) transitions, \( O(n) \) for each, yielding \( O(2^n \cdot n^3) \).

---

##### **1.b. Example of Suboptimal 2-Approximation for Metric TSP**
- **Example**:
  - A triangle graph with vertices \( A, B, C \) and weights:
    - \( d(A, B) = 1 \), \( d(B, C) = 1 \), \( d(A, C) = 2 \).
  - Optimal TSP: \( A \to B \to C \to A \), cost \( 4 \).
  - MST-based 2-approximation:
    - MST: \( A-B, B-C \), cost \( 2 \).
    - TSP tour: \( A \to B \to C \to A \), cost \( 4 \).
    - Adding \( A-C \), cost increases to \( 6 \).

---

##### **1.c. Worst Case for \( \text{Greedy-IS} \)**
- **Objective**: Construct a graph where \( \text{Greedy-IS} \) performs poorly.
- **Example**:
  - Graph: A star with center \( C \) and \( n-1 \) leaves.
  - **Maximum Independent Set**:
    - All \( n-1 \) leaves.
  - **Greedy-IS**:
    - Finds the center \( C \) as part of the vertex cover, leaving only one leaf in the independent set.
  - Approximation Ratio:
    - \( \frac{1}{n-1} \), which is asymptotically poor.

---

#### **Problem 2: Eulerian Path**
---

##### **2.a. Adding a Road for Hotel Humperdink**
- **Objective**: Ensure Eulerian Path from Humperdink’s hotel to Central Plaza.
- **Approach**:
  - Add a road connecting Humperdink’s hotel to a vertex with odd degree (other than Central Plaza).
  - This ensures all vertices except two (start and end) have even degree.

---

##### **2.b. Adding a Road for Motel Mildred**
- **Objective**: Mildred’s guests can traverse the graph, but not Humperdink’s.
- **Approach**:
  - Add a road creating an Eulerian Path for Mildred’s hotel, ensuring no Eulerian Path exists for Humperdink’s graph by introducing odd-degree vertices specific to his routes.

---

##### **2.c. Proof of Eulerian Path Conditions**
- **Statement**: A graph \( G \) has an Eulerian Path if and only if:
  - \( G \) is connected.
  - Exactly two vertices have odd degree (start and end points).
- **Proof**:
  - **Necessity**:
    - If \( G \) has an Eulerian Path, the degree of all vertices must balance except start and end, which can differ by 1 (odd degrees).
  - **Sufficiency**:
    - Start at an odd-degree vertex; traverse edges exactly once.
    - Path terminates at the other odd-degree vertex.

---

#### **Problem 3: Group Admission in a Museum**
---

##### **3.a. Greedy Algorithm is a 2-Approximation**
- **Algorithm**:
  - Sort groups \( G \) by size in descending order.
  - Admit groups if their size fits the remaining capacity.
- **Proof**:
  - Optimal solution maximizes total admitted size \( \leq n \).
  - Greedy ensures at least \( \frac{1}{2} \) of optimal by prioritizing largest groups.

---

##### **3.b. Counterexample for Greedy Algorithm**
- **Example**:
  - Museum capacity: \( n = 100 \).
  - Groups: \( [99, 98, 2, 2, 2, ..., 2] \).
  - Greedy admits \( 99 \), leaves \( 1 \) capacity.
  - Optimal admits \( 2, 2, 2, ..., 2 \) (50 groups), total 100.
  - Greedy achieves only \( \frac{1}{2} \) of optimal.

---

##### **3.c. Space-Efficient Algorithm**
- **Objective**: Compute a 2-approximation using \( O(1) \) space.
- **Approach**:
  1. Compute the total capacity needed by large groups \( \leq n \).
  2. Compare with small groups:
     - Admit as many small groups as possible without sorting.
  3. Result: \( O(m) \) time, constant space.

