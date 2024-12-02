### Detailed Solution for Problem S-1: Spanning Tree with Exactly \( k \) Blue Edges

---

#### **Problem Restatement**
Given a graph \( G = (V, E) \) with \( n \) nodes and \( m \) edges:
1. Each edge is colored either **blue** or **red**.
2. We need to construct a spanning tree with:
   - Exactly \( k \) blue edges.
   - Exactly \( n - k - 1 \) red edges.

Provide an algorithm, its correctness proof, and the running time.

---

#### **Solution**

### **Algorithm**
We can solve this problem using a modified version of **Kruskal's Algorithm** for Minimum Spanning Trees:

1. **Preprocessing**:
   - Partition edges into:
     - \( E_b \): Set of blue edges.
     - \( E_r \): Set of red edges.

2. **Validation**:
   - Check if \( k \leq n-1 \). If \( k > n-1 \), output "No solution" because it's impossible to form a spanning tree with \( n-1 \) edges using \( k \) blue edges.

3. **Modified Kruskal's Algorithm**:
   - Sort \( E_b \) and \( E_r \) by weight (or arbitrarily if weights are not provided).
   - Use a **union-find structure** to ensure the spanning tree is valid (no cycles).
   - Construct the spanning tree as follows:
     1. **Add Blue Edges**:
        - Add edges from \( E_b \) to the spanning tree until \( k \) blue edges are included.
        - If \( E_b \) has fewer than \( k \) edges or adding \( k \) blue edges leads to a cycle, terminate with "No solution."
     2. **Add Red Edges**:
        - Add edges from \( E_r \) to fill the remaining \( n-k-1 \) edges, ensuring no cycles.

4. **Output**:
   - Return the constructed spanning tree if it has \( n-1 \) edges with exactly \( k \) blue edges and \( n-k-1 \) red edges.

---

### **Correctness Proof**
1. **Spanning Tree Conditions**:
   - A spanning tree in a graph with \( n \) nodes has exactly \( n-1 \) edges.
   - The algorithm ensures \( n-1 \) edges by:
     - Adding \( k \) blue edges.
     - Adding \( n-k-1 \) red edges.

2. **Cycle-Free Guarantee**:
   - The union-find structure ensures that edges are added only if they do not form a cycle, satisfying the spanning tree property.

3. **Exact \( k \) Blue Edges**:
   - By controlling the number of edges added from \( E_b \), the algorithm ensures exactly \( k \) blue edges are included.

4. **Feasibility Check**:
   - If \( k > n-1 \) or \( E_b \) has fewer than \( k \) usable edges, the algorithm correctly identifies that no solution exists.

---

### **Running Time Analysis**
1. **Edge Partitioning**:
   - Partition \( E \) into \( E_b \) and \( E_r \): \( O(m) \).

2. **Sorting**:
   - Sort \( E_b \) and \( E_r \): \( O(m \log m) \).

3. **Modified Kruskal's Algorithm**:
   - Union-find operations:
     - \( O(\alpha(n)) \) per operation, where \( \alpha(n) \) is the inverse Ackermann function (very small, almost constant).
     - Total: \( O(m \cdot \alpha(n)) \).

4. **Total Complexity**:
   - \( O(m \log m + m \cdot \alpha(n)) = O(m \log m) \).

---

### **Example**
**Input**:
- \( G \) with \( n = 5 \), \( m = 7 \).
- Blue edges: \( (a, b), (b, c), (c, d) \).
- Red edges: \( (a, c), (b, d), (d, e), (a, e) \).
- \( k = 2 \).

**Steps**:
1. Partition edges:
   - \( E_b = \{(a, b), (b, c), (c, d)\} \), \( E_r = \{(a, c), (b, d), (d, e), (a, e)\} \).
2. Sort edges by weight (if weights exist).
3. Add blue edges:
   - Add \( (a, b) \), \( (b, c) \).
4. Add red edges:
   - Add \( (a, e), (d, e) \).
5. Result:
   - Spanning tree with \( k = 2 \) blue edges and \( n-k-1 = 2 \) red edges.

