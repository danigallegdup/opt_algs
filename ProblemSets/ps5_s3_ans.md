### Solution for Question 3: Minimum Cut Edge Directionality

---

#### **Problem Restatement**
Let \( (u, v) \) be an edge in a flow network \( G = (V, E) \). Prove that if there is a minimum (s, t)-cut \( (S, T) \) such that \( u \in S \) and \( v \in T \), then no minimum (s, t)-cut \( (S', T') \) exists where \( u \in T' \) and \( v \in S' \).

---

### **Solution**

#### **Key Idea**
- Use the **Max-Flow Min-Cut Theorem** to prove the directionality of edges in the cut is preserved.
- An edge \( (u, v) \) crossing from \( S \) to \( T \) in a minimum cut contributes positively to the cut's capacity. Reversing this direction would violate the flow conservation property or result in a higher cut capacity.

---

### **Proof**

1. **Definitions**:
   - \( S, T \): Partition of vertices for a minimum cut such that \( S \cap T = \emptyset \), \( S \cup T = V \).
   - Cut edges: Edges crossing from \( S \) to \( T \), i.e., \( (u, v) \) where \( u \in S, v \in T \).
   - Capacity of the cut:
     \[
     C(S, T) = \sum_{(u, v) \in E, u \in S, v \in T} c(u, v),
     \]
     where \( c(u, v) \) is the capacity of edge \( (u, v) \).

2. **Case Analysis**:
   - Suppose \( (u, v) \) is an edge in the minimum cut with \( u \in S \) and \( v \in T \).
   - To have another minimum cut \( (S', T') \) with \( u \in T' \) and \( v \in S' \), the edge \( (u, v) \) would now cross from \( T' \) to \( S' \).

3. **Implication of Reversing Direction**:
   - In \( (S, T) \), the edge \( (u, v) \) contributes \( c(u, v) \) to the cut capacity.
   - In \( (S', T') \), reversing \( u \) and \( v \) means:
     - The edge \( (u, v) \) no longer contributes to the cut capacity.
     - Instead, \( (v, u) \) would need to contribute, but this is impossible since residual capacity \( c^r(v, u) = 0 \) in a maximum flow.

4. **Contradiction**:
   - The existence of \( (S', T') \) with \( u \in T' \) and \( v \in S' \) implies either:
     - A cut with lower capacity than \( C(S, T) \), contradicting the minimality of \( (S, T) \).
     - A violation of flow conservation across \( (S', T') \).

5. **Conclusion**:
   - No minimum cut \( (S', T') \) exists where \( u \in T' \) and \( v \in S' \) if \( u \in S \) and \( v \in T \) in another minimum cut.

---

### **Intuition**
- The directionality of edges crossing the cut in a minimum (s, t)-cut is fixed by the residual capacity in the flow network. Reversing the direction of any edge in a valid minimum cut would violate the capacity condition.

---

### **Example**

#### **Graph**:
- Vertices: \( V = \{s, u, v, t\} \),
- Edges and capacities:
  \[
  (s, u) = 10, \quad (u, v) = 5, \quad (v, t) = 10.
  \]

#### **Steps**:
1. Compute max-flow:
   - Flow saturates \( (u, v) \) in the max-flow computation.

2. Minimum cut:
   - \( S = \{s, u\} \), \( T = \{v, t\} \).
   - Cut edges: \( (u, v) \).

3. Check for reversal:
   - If \( u \in T' \) and \( v \in S' \), the edge \( (u, v) \) would violate the residual capacity, as no flow can be pushed back from \( v \) to \( u \).

---

### **Relevant Lecture Content**
- **Max-Flow Min-Cut Theorem**:
  - Connection between flow conservation and cut capacities.
- **Residual Graphs**:
  - Role of residual capacities in determining edge directionality.
- **Graph Partitioning**:
  - Properties of vertex partitions in minimum cuts.

