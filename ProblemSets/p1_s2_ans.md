### Detailed Solution for Problem S-2: Removing Minimum Edges to Make the Graph Triangle-Free

---

#### **Problem Restatement**
Given an undirected graph \( G = (V, E) \), remove the minimum number of edges such that the residual graph contains no triangles. The solution should be a **3-approximation algorithm** that runs in polynomial time.

---

#### **Solution Approach**

### **Algorithm: Greedy Triangle Removal**
The problem is NP-hard, so we use a greedy approximation algorithm.

1. **Identify Triangles**:
   - Enumerate all triangles in the graph. A triangle is a triplet \( (a, b, c) \) such that:
     - \( (a, b), (b, c), (a, c) \in E \).

2. **Remove Edges**:
   - For each triangle:
     - Remove the edge that appears in the maximum number of triangles (greedy choice).
   - Update the graph after each removal (i.e., recheck triangles).

3. **Repeat Until Triangle-Free**:
   - Continue identifying triangles and removing edges until no triangles remain in the graph.

---

### **Approximation Analysis**

#### **Key Insight**:
- **Optimal Solution**:
  - To remove all triangles, at least one edge per triangle must be removed. Let \( OPT \) denote the minimum number of edges removed in an optimal solution.
- **Greedy Algorithm**:
  - The greedy algorithm may remove up to 3 edges per triangle. Thus, the total number of edges removed by the greedy approach is at most \( 3 \cdot OPT \), giving a 3-approximation.

---

### **Correctness Proof**
1. **Triangle-Free Guarantee**:
   - By definition, removing at least one edge from every triangle ensures no triangles remain in the graph.
   - The algorithm identifies and processes all triangles iteratively, so the final graph is triangle-free.

2. **Approximation Bound**:
   - Each triangle requires at least one edge removal in the optimal solution.
   - The greedy algorithm may remove up to 3 edges for each triangle, ensuring a \( 3 \cdot OPT \) bound.

---

### **Time Complexity Analysis**
1. **Triangle Detection**:
   - Enumerating all triangles using adjacency lists:
     - \( O(n^3) \) for naive enumeration.
     - Faster algorithms exist using matrix multiplication \( O(n^{2.372}) \) or adjacency list processing.

2. **Edge Removal**:
   - Removing edges and updating the graph: \( O(m) \) per triangle.

3. **Total Complexity**:
   - \( O(T \cdot (n^2 + m)) \), where \( T \) is the number of triangles in the graph.

For sparse graphs, the complexity is approximately \( O(n^2) \).

---

### **Example**
#### **Input**:
Graph \( G = (V, E) \):
- \( V = \{a, b, c, d\} \)
- \( E = \{(a, b), (b, c), (c, a), (b, d), (c, d)\} \)

#### **Steps**:
1. **Identify Triangles**:
   - \( (a, b, c) \): Edges \( (a, b), (b, c), (c, a) \).
   - \( (b, c, d) \): Edges \( (b, c), (c, d), (b, d) \).

2. **Remove Edges**:
   - From \( (a, b, c) \), remove \( (b, c) \) (shared with the second triangle).
   - Recheck triangles:
     - \( (b, d, c) \) now only contains \( (c, d), (b, d) \), so remove \( (b, d) \).

3. **Output**:
   - Residual graph: \( \{(a, b), (c, d)\} \).
   - Total edges removed: 2.

