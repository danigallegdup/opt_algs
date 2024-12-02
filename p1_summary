### Summarized Solutions for Problem Set 1

---

#### **S-1: Spanning Tree with Exactly \( k \) Blue Edges**
**Problem**: Construct a spanning tree with exactly \( k \) blue edges and \( n-k-1 \) red edges in a graph \( G = (V, E) \).

**Solution Approach**:
1. **Initial Validation**:
   - Verify that \( k \leq n-1 \). If \( k > n-1 \), no valid spanning tree exists.
2. **Divide Edges**:
   - Partition \( E \) into \( E_b \) (blue edges) and \( E_r \) (red edges).
3. **Construct Minimum Spanning Tree**:
   - Use a modified Kruskal’s algorithm:
     1. Sort \( E_b \) and \( E_r \) by weight (if weights are provided).
     2. Add blue edges from \( E_b \) to the spanning tree until \( k \) blue edges are included.
     3. Fill remaining edges of the tree (\( n-k-1 \)) with red edges from \( E_r \), ensuring no cycles.
4. **Correctness**:
   - The resulting tree will have exactly \( k \) blue edges due to the greedy selection process, and it is a valid spanning tree because cycles are avoided.
5. **Time Complexity**:
   - Sorting edges: \( O(m \log m) \).
   - Constructing the tree: \( O(m \log n) \) using a union-find structure.

---

#### **S-2: Triangle-Free Graph by Removing Minimum Edges**
**Problem**: Remove the minimum number of edges from \( G \) such that no triangles remain.

**Solution Approach**:
1. **Greedy Triangle Removal**:
   - Identify all triangles in the graph.
   - For each triangle \( (a, b, c) \):
     1. Remove the edge involved in the maximum number of triangles.
2. **Algorithm**:
   - Repeat until no triangles are left in the graph.
   - Each edge removal reduces the number of triangles.
3. **Approximation**:
   - Guarantees a 3-approximation:
     - The optimal solution removes at least one edge from each triangle.
     - The greedy approach removes at most three edges per triangle, ensuring the solution is at most three times the optimal.
4. **Time Complexity**:
   - Triangle enumeration: \( O(n^3) \) (or faster using adjacency matrices).
   - Edge removal and updates: \( O(m) \) per iteration.

---

#### **S-3: Finding Maximal Points in the Plane**
**Problem**: Determine the set of maximal points in \( P \) using the Kirkpatrick-Seidel algorithm.

##### **3.a Prove Correctness**
- **Proof**:
  1. **Divide and Conquer**:
     - Splits points into two halves by the median \( x \)-coordinate.
  2. **Maximality of \( q \)**:
     - The highest \( y \)-coordinate point in \( P_r \) is guaranteed to be maximal.
  3. **Recursive Calls**:
     - Removing points dominated by \( q \) ensures no dominated points remain in either half.
  4. **Combining Results**:
     - The union of maximal points from \( P_\ell \), \( P_r \), and \( q \) forms the set of maximal points.

##### **3.b Prove Time Complexity \( O(n \log n) \)**
- **Proof**:
  1. **Splitting Points**:
     - Computing the median takes \( O(n) \) using a linear-time selection algorithm.
  2. **Recursive Splits**:
     - Dividing points into \( P_\ell \) and \( P_r \) is linear.
  3. **Recursive Relation**:
     - T(n) = \( 2T(n/2) + O(n) \).
     - Solving gives \( T(n) = O(n \log n) \).

##### **3.c Prove Time Complexity \( O(n \log h) \)**
- **Proof**:
  1. **Observation**:
     - Only \( h \) maximal points are added.
  2. **Unbalanced Recursion**:
     - When most points are dominated, recursion depth depends on \( h \), not \( n \).
  3. **Instance-Specific Recursion**:
     - T(n) = \( T(n-h) + O(h \log h) \), which simplifies to \( O(n \log h) \).

