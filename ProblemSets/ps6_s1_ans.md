### Solution for Question 1: Proof of Kőnig’s Theorem

---

#### **Problem Statement**
Prove Kőnig’s Theorem:
- In any bipartite graph \( G = (U \cup V, E) \), the size of a **maximum matching** is equal to the size of a **minimum vertex cover**.

---

### **Solution**

#### **Definitions**
1. **Matching**:
   - A set of edges \( M \subseteq E \) such that no two edges in \( M \) share a common vertex.

2. **Vertex Cover**:
   - A set of vertices \( C \subseteq V \) such that every edge \( e \in E \) is incident to at least one vertex in \( C \).

3. **Kőnig’s Theorem**:
   - For bipartite graphs:
     \[
     | \text{Maximum Matching} | = | \text{Minimum Vertex Cover} |.
     \]

---

### **Proof Outline**

1. **Construct a Flow Network**:
   - Treat \( G \) as a flow network:
     - Add a source \( s \) and sink \( t \).
     - Connect:
       - \( s \to u \) for all \( u \in U \),
       - \( v \to t \) for all \( v \in V \),
       - \( u \to v \) for all \( (u, v) \in E \).
     - Assign capacity 1 to all edges.

2. **Maximum Flow Equals Maximum Matching**:
   - Use a max-flow algorithm to compute the maximum flow \( f \).
   - The flow value \( |f| \) corresponds to the size of the maximum matching \( M \) in \( G \):
     - Each unit of flow represents a distinct edge in the matching.

3. **Max-Flow Min-Cut Theorem**:
   - By the Max-Flow Min-Cut theorem:
     - The value of the maximum flow \( |f| \) equals the capacity of the minimum cut \( (S, T) \) in the flow network.

4. **Minimum Cut Corresponds to Minimum Vertex Cover**:
   - In the bipartite graph:
     - The reachable set \( S \) from \( s \) in the residual graph represents vertices not in the vertex cover.
     - The non-reachable set \( T \) identifies vertices in the vertex cover.
   - The size of the minimum cut equals the number of edges in the minimum vertex cover.

5. **Equality**:
   - Since the maximum matching \( |M| \) equals the maximum flow \( |f| \), and the minimum vertex cover \( |C| \) equals the minimum cut capacity, we conclude:
     \[
     | \text{Maximum Matching} | = | \text{Minimum Vertex Cover} |.
     \]

---

### **Example**

#### **Graph**:
- Bipartite graph \( G = (U \cup V, E) \):
  - \( U = \{u_1, u_2\}, V = \{v_1, v_2, v_3\} \),
  - \( E = \{(u_1, v_1), (u_1, v_2), (u_2, v_3)\} \).

#### **Steps**:
1. Compute the maximum matching:
   - Matching \( M = \{(u_1, v_1), (u_2, v_3)\} \), size = 2.
2. Compute the minimum vertex cover:
   - Vertex cover \( C = \{u_1, v_3\} \), size = 2.

**Result**:
- \( | \text{Maximum Matching} | = 2 \),
- \( | \text{Minimum Vertex Cover} | = 2 \).

---

### **Relevant Lecture Content**
- **Max-Flow Min-Cut Theorem**:
  - Applications in bipartite graphs.
- **Matching and Cover Duality**:
  - Relationship between maximum matchings and minimum vertex covers.

Let me know if you'd like further clarifications!
