### **Ultimate Cheat Sheet: Definitions and Equations for Network Flow and Optimization**

---

### **1. Graph Theory Basics**
- **Graph**: \( G = (V, E) \), where \( V \) is a set of vertices and \( E \) is a set of edges.
- **Directed Graph**: Edges have a direction, \( (u, v) \neq (v, u) \).
- **Bipartite Graph**: \( V \) can be divided into two disjoint sets \( U, W \), and all edges connect vertices from \( U \) to \( W \).

---

### **2. Maximum Flow and Minimum Cut**
#### **Key Definitions**:
- **Flow**: \( f(u, v) \): Amount of flow along edge \( (u, v) \), subject to:
  1. **Capacity Constraint**: \( 0 \leq f(u, v) \leq c(u, v) \).
  2. **Flow Conservation**: \( \sum_{v \in V} f(u, v) = \sum_{v \in V} f(v, u) \) for \( u \neq s, t \).
- **Residual Capacity**: \( c^r(u, v) = c(u, v) - f(u, v) \).
- **Cut**: A partition \( (S, T) \) of \( V \), where \( s \in S \) and \( t \in T \).
- **Cut Capacity**:
  \[
  C(S, T) = \sum_{u \in S, v \in T} c(u, v).
  \]

#### **Theorem**: **Max-Flow Min-Cut**
- The maximum flow \( f \) equals the capacity of the minimum cut:
  \[
  |f| = C(S, T).
  \]

#### **Algorithms**:
- **Ford-Fulkerson**:
  - Augmenting paths via DFS/BFS.
  - Complexity: \( O(E \cdot |f|) \).
- **Edmonds-Karp**:
  - BFS-based, \( O(VE^2) \).
- **Push-Relabel**:
  - Relabel vertices to improve flow, \( O(V^2E) \).

---

### **3. Matchings**
#### **Key Definitions**:
- **Matching**: Set of edges such that no two edges share a vertex.
- **Maximum Matching**: Largest possible matching.
- **Perfect Matching**: Matching covering all vertices in a bipartite graph.
- **Vertex Cover**: Set of vertices covering all edges.

#### **Kőnig’s Theorem**:
- In bipartite graphs:
  \[
  | \text{Maximum Matching} | = | \text{Minimum Vertex Cover} |.
  \]

#### **Algorithms**:
- Hopcroft-Karp for Maximum Matching:
  - Complexity: \( O(\sqrt{V} \cdot E) \).

---

### **4. Cuts and Covers**
- **Vertex Cover**: Set of vertices covering all edges.
- **Edge Cover**: Set of edges covering all vertices.
- **Minimum Cut**:
  - Partition \( V \) into \( S, T \) to minimize \( C(S, T) \).

---

### **5. Probabilistic Methods**
#### **Randomized Approximation**:
- **Maximum \( k \)-Cut**:
  - Randomly assign vertices to \( k \) partitions.
  - Approximation ratio: \( \frac{k-1}{k} \).
- **MAX DI-CUT**:
  - Randomly assign vertices to two subsets.
  - Approximation ratio: \( \frac{1}{4} \).

#### **Lovász Local Lemma (LLL)**:
- **Symmetric Form**:
  - If \( P(A_i) \leq p \) and \( ep(d+1) \leq 1 \), there exists a nonzero probability that none of the events \( A_i \) occur.

---

### **6. Linear Programming and LP Relaxation**
#### **Linear Programming (LP)**:
- **Form**:
  \[
  \text{Maximize/Minimize } c^T x \quad \text{subject to } Ax \leq b, \, x \geq 0.
  \]
- **Relaxation**:
  - Allow fractional solutions, then round.

#### **Applications**:
1. **Vertex Cover**:
   - LP relaxation and rounding for approximate solutions.
2. **MAX DI-CUT**:
   - LP rounding achieves \( \frac{1}{2} \)-approximation.

---

### **7. Hypergraph 2-Colorability**
- **Uniform Hypergraph**:
  - \( \Delta \leq \frac{2^{k-3}}{k-1} \) ensures 2-colorability using LLL.
- **Non-Uniform Hypergraph**:
  - Dependency constraint:
    \[
    \sum_{f \neq e, f \cap e \neq \emptyset} 2^{-|f|} \leq \frac{1}{8}.
    \]

---

### **8. Menger’s Theorem**
- In any graph:
  - **Vertex Connectivity**: Minimum number of vertices to remove to disconnect \( s \) and \( t \).
  - Equals the maximum number of pairwise disjoint paths between \( s \) and \( t \).

---

### **9. Cycle Covers**
- **Cycle Cover**: Set of vertex-disjoint cycles covering all vertices.
- **Algorithm**:
  - Convert graph to bipartite form and find a perfect matching.

---

### **10. Key Equations Summary**
1. **Flow Conservation**:
   \[
   \sum_{v \in V} f(u, v) = \sum_{v \in V} f(v, u), \, u \neq s, t.
   \]
2. **Cut Capacity**:
   \[
   C(S, T) = \sum_{u \in S, v \in T} c(u, v).
   \]
3. **LLL Symmetric Form**:
   \[
   ep(d+1) \leq 1.
   \]
4. **Max-Flow = Min-Cut**:
   \[
   |f| = C(S, T).
   \]

---

This cheatsheet consolidates the critical definitions, theorems, and equations of the course for quick reference and review. Let me know if you need additional explanations for any section!
