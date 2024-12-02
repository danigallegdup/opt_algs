### Full Solution for Problem 1: Travelling Salesman Problem and Independent Set
---

#### **1.a. TSP Algorithm in \( O(2^n \cdot n^3) \)**

##### **Problem Restatement**:
Solve the **Traveling Salesman Problem (TSP)** in a graph with \( n \) nodes and edge weights. The goal is to find the minimum-cost tour that visits every node exactly once and returns to the starting node. Use dynamic programming to achieve \( O(2^n \cdot n^3) \) time complexity.

---

##### **Algorithm: Dynamic Programming**
1. **Bitmask Representation**:
   - Use a bitmask to represent subsets of cities.
   - \( dp[S][v] \): The minimum cost to visit all cities in \( S \) (represented by the bitmask) and end at city \( v \).

2. **Initialization**:
   - Base case: Starting at the source node (city 0):
     \[
     dp[\{0\}][0] = 0
     \]
     Other \( dp[S][v] = \infty \) for all subsets \( S \) and cities \( v \).

3. **Recursive Transition**:
   - For each subset \( S \) containing \( v \) and for each \( u \in S \setminus \{v\} \):
     \[
     dp[S][v] = \min_{u \in S, u \neq v} \{dp[S \setminus \{v\}][u] + dist(u, v)\}.
     \]

4. **Final Step**:
   - Find the minimum cost to complete the tour by returning to the start city:
     \[
     \text{Result} = \min_{v \in V} \{dp[\{1, \dots, n\}][v] + dist(v, 0)\}.
     \]

---

##### **Complexity Analysis**:
- Subsets: There are \( 2^n \) subsets of \( n \) cities.
- Cities: For each subset, compute values for \( n \) cities.
- Transitions: For each city \( v \), check \( n-1 \) possible preceding cities in \( O(n) \).
- Total: \( O(2^n \cdot n^2 \cdot n) = O(2^n \cdot n^3) \).

---

#### **1.b. Example of Suboptimal 2-Approximation for Metric TSP**

##### **Problem Restatement**:
Provide an example where the **2-approximation algorithm** for metric TSP does not yield the optimal solution.

---

##### **Example**:
1. **Graph Setup**:
   - \( G = \{A, B, C\} \).
   - Distances:
     - \( d(A, B) = 1 \), \( d(B, C) = 1 \), \( d(A, C) = 2 \).
   - Metric property: Triangle inequality holds.

2. **Optimal TSP Solution**:
   - Tour: \( A \to B \to C \to A \).
   - Cost: \( 4 \).

3. **2-Approximation Algorithm**:
   - Construct MST: \( A-B, B-C \), cost \( 2 \).
   - Double the MST edges to form a tour: \( A \to B \to C \to A \), cost \( 4 \).
   - Add a shortcut to \( A-C \), increasing cost to \( 6 \).

4. **Observation**:
   - The 2-approximation algorithm produces a cost of \( 6 \) versus the optimal \( 4 \).

---

#### **1.c. Worst Case for Greedy Independent Set**

##### **Problem Restatement**:
Provide an example graph where the **Greedy-IS** algorithm for finding a maximum independent set performs poorly.

---

##### **Example**:
1. **Graph Setup**:
   - A star graph \( G \):
     - Center vertex \( C \).
     - \( n-1 \) leaf vertices connected only to \( C \).

2. **Optimal Independent Set**:
   - All \( n-1 \) leaf vertices: Maximum independent set size is \( n-1 \).

3. **Greedy-IS** Algorithm**:
   - Step 1: Run \( \text{Greedy-Match-VC} \):
     - Select the center \( C \) as part of the vertex cover (covers all edges).
   - Step 2: \( I = V \setminus C \):
     - Only one leaf vertex is in the independent set.

4. **Approximation Ratio**:
   - Independent set size from Greedy-IS: \( 1 \).
   - Optimal independent set size: \( n-1 \).
   - Ratio: \( \frac{1}{n-1} \), which approaches 0 as \( n \to \infty \).

---

### **Conclusion**
1. **TSP Dynamic Programming**:
   - Bitmask DP achieves \( O(2^n \cdot n^3) \), exploring all subsets efficiently.
2. **Suboptimal Example for TSP Approximation**:
   - Metric TSP 2-approximation can produce worse results due to shortcuts or doubled edges.
3. **Independent Set Approximation**:
   - Greedy-IS is ineffective for graphs where the optimal independent set is significantly larger than the complement of a minimal vertex cover. 
