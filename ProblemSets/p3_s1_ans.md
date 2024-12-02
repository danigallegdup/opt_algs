### Full Solution for Problem 1: Maximum \( k \)-Cut Problem

---

#### **Problem Restatement**
Given a graph \( G = (V, E) \) with weighted edges \( w(e) \geq 0 \), partition the vertices \( V \) into \( k \) disjoint subsets \( V_1, V_2, \dots, V_k \) such that the sum of the weights of the edges connecting vertices in different subsets is maximized.

---

### **Algorithm: Randomized \( \frac{k-1}{k} \)-Approximation**

#### **Steps**:
1. **Random Partitioning**:
   - Assign each vertex \( v \in V \) to one of \( k \) partitions uniformly at random.

2. **Weight Calculation**:
   - For each edge \( e = (u, v) \):
     - If \( u \) and \( v \) are in different partitions (\( V_i \neq V_j \)), add the edge weight \( w(e) \) to the total cut weight.

---

#### **Analysis of the Approximation Factor**

1. **Key Idea**:
   - Each edge \( e = (u, v) \) has a \( \frac{k-1}{k} \) probability of being included in the cut because:
     - The probability that \( u \) and \( v \) are assigned to different partitions is \( 1 - \frac{1}{k} = \frac{k-1}{k} \).

2. **Expected Cut Weight**:
   - For each edge \( e = (u, v) \), its contribution to the expected cut weight is:
     \[
     \text{Expected Weight Contribution} = w(e) \cdot \frac{k-1}{k}.
     \]

3. **Approximation Factor**:
   - The randomized algorithm achieves an expected total cut weight:
     \[
     \mathbb{E}[\text{Cut Weight}] = \frac{k-1}{k} \cdot \text{OPT},
     \]
     where \( \text{OPT} \) is the weight of the optimal \( k \)-cut.

---

### **Correctness and Complexity**

#### **Correctness**:
- The algorithm guarantees an expected weight that is \( \frac{k-1}{k} \) of the optimal solution.
- The use of random assignment ensures fairness and uniform probability distribution across partitions.

#### **Complexity**:
1. **Random Assignment**:
   - Assigning \( n \) vertices to \( k \) partitions takes \( O(n) \).
2. **Weight Calculation**:
   - Iterating through \( m \) edges to compute the total cut weight takes \( O(m) \).
3. **Total Time Complexity**:
   - \( O(n + m) \), linear in the size of the graph.

---

### **Example**

#### **Graph**:
- Vertices: \( V = \{A, B, C, D\} \).
- Edges and Weights:
  \[
  E = \{(A, B, 3), (A, C, 2), (B, C, 1), (C, D, 4)\}.
  \]

#### **Partitions**:
- Randomly assign:
  - \( A \to V_1 \), \( B \to V_2 \), \( C \to V_3 \), \( D \to V_1 \).

#### **Cut Calculation**:
- Edges in the cut:
  - \( (A, B) \): \( A \in V_1, B \in V_2 \), weight = 3.
  - \( (A, C) \): \( A \in V_1, C \in V_3 \), weight = 2.
  - \( (C, D) \): \( C \in V_3, D \in V_1 \), weight = 4.
- Total cut weight = \( 3 + 2 + 4 = 9 \).

---

### **Relevant Lecture Content**
- **Randomized Approximation Algorithms**:
  - Probabilistic guarantees in optimization problems.
  - Use of random assignments for partitioning and maximization problems.

