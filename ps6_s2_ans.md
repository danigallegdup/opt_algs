### Solution for Question 2: Disrupting Maximum Flow with Edge Deletion

---

#### **Problem Statement**
In a flow network \( G = (V, E) \) with edge capacities of 1, find a set of exactly \( k \) edges to delete such that the maximum flow from source \( s \) to sink \( t \) is minimized.

---

### **Solution Outline**

#### **Key Concepts**
1. **Max-Flow Min-Cut Theorem**:
   - The maximum flow \( f \) in the network is equal to the capacity of the minimum cut \( (S, T) \), where:
     \[
     C(S, T) = \sum_{u \in S, v \in T} c(u, v).
     \]

2. **Edge Deletion Impact**:
   - Deleting an edge reduces the residual capacity of the graph.
   - To minimize the maximum flow, prioritize deleting edges that belong to the minimum cut.

---

### **Algorithm**

1. **Compute Maximum Flow**:
   - Use a standard max-flow algorithm (e.g., Ford-Fulkerson or Edmonds-Karp) to compute the maximum flow \( f \).

2. **Identify Minimum Cut**:
   - Construct the residual graph after computing \( f \).
   - Perform a BFS or DFS from \( s \) to find the set of reachable vertices \( S \).
   - Define the cut as edges crossing from \( S \) to \( T = V \setminus S \).

3. **Select \( k \) Edges to Delete**:
   - Rank edges in the minimum cut \( (S, T) \) by their capacity.
   - Select the \( k \) edges to delete that belong to the minimum cut.

4. **Update Flow**:
   - Deleting edges reduces the capacity of the minimum cut, directly decreasing the maximum flow.

---

### **Correctness**

1. **Impact on Flow**:
   - Deleting an edge in the minimum cut reduces the cut capacity and thus the maximum flow.
   - Deleting \( k \) edges ensures that the new flow value \( f' \leq f - k \).

2. **Optimality**:
   - Deleting edges outside the minimum cut does not directly impact the maximum flow, ensuring that edge deletions are focused on the critical cut edges.

---

### **Complexity Analysis**

1. **Compute Max-Flow**:
   - Time complexity depends on the algorithm used:
     - \( O(VE^2) \) for Edmonds-Karp or \( O(E^2 \sqrt{V}) \) for Push-Relabel.
2. **Identify Minimum Cut**:
   - BFS or DFS in the residual graph: \( O(V + E) \).
3. **Edge Selection**:
   - Selecting \( k \) edges from the cut: \( O(k \log E) \) if sorting is needed.

**Total Complexity**:
- Dominated by the max-flow computation: \( O(VE^2) \) or \( O(E^2 \sqrt{V}) \).

---

### **Example**

#### **Graph**:
- \( V = \{s, a, b, c, t\} \),
- Edges and capacities:
  \[
  E = \{(s, a, 1), (s, b, 1), (a, c, 1), (b, c, 1), (c, t, 2)\}.
  \]

#### **Steps**:
1. Compute max-flow:
   - Maximum flow \( f = 2 \).

2. Identify minimum cut:
   - \( S = \{s, a, b\} \), \( T = \{c, t\} \),
   - Minimum cut edges: \( \{(a, c), (b, c)\} \).

3. Select \( k = 1 \) edge to delete:
   - Delete \( (a, c) \) or \( (b, c) \), reducing the cut capacity by 1.

4. New max-flow:
   - After deleting \( (a, c) \), the maximum flow reduces to \( f' = 1 \).

---

### **Relevant Lecture Content**
- **Max-Flow Min-Cut Theorem**:
  - Relationship between cuts and flows in network optimization.
- **Edge Prioritization**:
  - Strategies to reduce flow capacity via critical edge deletions.

Let me know if you need further details or examples!
