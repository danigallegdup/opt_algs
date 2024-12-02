### Solution for Question 3: Detecting Cycle Covers

---

#### **Problem Statement**
Design an algorithm to determine whether a directed graph \( G = (V, E) \) has a **cycle cover**, i.e., a set of vertex-disjoint cycles that cover all vertices in the graph. If such a cycle cover exists, construct it.

---

### **Solution Outline**

#### **Key Idea**
A directed graph \( G = (V, E) \) has a cycle cover if and only if it has a **perfect matching** in a corresponding bipartite graph representation.

---

#### **Algorithm Steps**

1. **Construct a Bipartite Graph**:
   - Create a bipartite graph \( G' = (V_1 \cup V_2, E') \), where:
     - \( V_1 \) and \( V_2 \) are two copies of \( V \) (original vertices in \( G \)).
     - For each directed edge \( (u, v) \in E \), add an edge \( (u \in V_1, v \in V_2) \) in \( G' \).

2. **Find a Perfect Matching**:
   - Use a maximum matching algorithm (e.g., Hopcroft-Karp or augmenting paths) to find a matching in \( G' \).
   - A perfect matching in \( G' \) ensures that every vertex in \( V_1 \) is matched to a vertex in \( V_2 \).

3. **Verify Cycle Cover**:
   - A perfect matching in \( G' \) corresponds to a valid assignment of outgoing edges from \( V_1 \) to incoming edges in \( V_2 \), forming vertex-disjoint cycles in \( G \).

4. **Construct the Cycle Cover**:
   - Trace cycles in \( G \) using the edges in the matching:
     - Start at any unmatched vertex.
     - Follow matched edges to form cycles until all vertices are covered.

---

### **Correctness**

#### **Cycle Cover and Perfect Matching Equivalence**:
1. A cycle cover ensures that every vertex is part of a cycle, implying a one-to-one correspondence between outgoing and incoming edges.
2. This one-to-one correspondence is equivalent to finding a perfect matching in \( G' \), where each vertex in \( V_1 \) maps uniquely to a vertex in \( V_2 \).

---

### **Complexity Analysis**

1. **Constructing \( G' \)**:
   - Time complexity: \( O(V + E) \), where \( E \) is the number of edges in \( G \).

2. **Finding Perfect Matching**:
   - Using Hopcroft-Karp: \( O(\sqrt{V} \cdot E) \).

3. **Cycle Construction**:
   - Traversing matched edges to construct cycles: \( O(V) \).

**Total Complexity**:
- \( O(\sqrt{V} \cdot E) \), dominated by the perfect matching computation.

---

### **Example**

#### **Graph**:
- \( V = \{A, B, C\} \),
- Directed edges: \( E = \{(A, B), (B, C), (C, A)\} \).

#### **Steps**:
1. Construct bipartite graph \( G' \):
   - \( V_1 = \{A_1, B_1, C_1\} \), \( V_2 = \{A_2, B_2, C_2\} \),
   - Edges: \( E' = \{(A_1, B_2), (B_1, C_2), (C_1, A_2)\} \).

2. Find perfect matching:
   - Matching: \( \{(A_1, B_2), (B_1, C_2), (C_1, A_2)\} \).

3. Construct cycle cover:
   - Trace cycles: \( A \to B \to C \to A \).

**Result**:
- \( G \) has a cycle cover: \( \{(A, B), (B, C), (C, A)\} \).

---

### **Relevant Lecture Content**
- **Perfect Matching in Bipartite Graphs**:
  - Maximum matching and vertex-disjoint cycle equivalence.
- **Graph Transformations**:
  - Conversion from directed graphs to bipartite representations.

