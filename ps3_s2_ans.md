### Full Solution for Problem 2: Maximum Directed Cut (MAX DI-CUT)

---

#### **Problem Restatement**
Given a directed graph \( G = (V, A) \) with edge weights \( w(i, j) \geq 0 \), partition the vertex set \( V \) into two disjoint subsets \( U \) and \( W = V \setminus U \) such that the total weight of arcs from \( U \) to \( W \) is maximized. Provide a randomized \( \frac{1}{4} \)-approximation algorithm.

---

### **Algorithm: Randomized Partitioning**

#### **Steps**:
1. **Random Assignment**:
   - For each vertex \( v \in V \), assign \( v \) to one of the subsets \( U \) or \( W \) with equal probability \( \frac{1}{2} \).

2. **Weight Calculation**:
   - For each arc \( (i, j) \in A \):
     - If \( i \in U \) and \( j \in W \), add the arc weight \( w(i, j) \) to the total cut weight.

---

### **Analysis of the Approximation Factor**

#### **Key Idea**:
- Each directed arc \( (i, j) \) contributes to the cut with a probability of \( \frac{1}{4} \) because:
  1. Probability that \( i \in U \): \( \frac{1}{2} \).
  2. Probability that \( j \in W \): \( \frac{1}{2} \).
  3. Independence of assignments:
     \[
     P(i \in U \text{ and } j \in W) = \frac{1}{2} \cdot \frac{1}{2} = \frac{1}{4}.
     \]

#### **Expected Cut Weight**:
- For each arc \( (i, j) \), its contribution to the expected cut weight is:
  \[
  \text{Expected Weight Contribution} = w(i, j) \cdot \frac{1}{4}.
  \]
- Summing over all arcs \( A \), the expected total cut weight is:
  \[
  \mathbb{E}[\text{Cut Weight}] = \frac{1}{4} \cdot \text{OPT},
  \]
  where \( \text{OPT} \) is the weight of the optimal directed cut.

#### **Approximation Factor**:
- The randomized algorithm achieves an approximation factor of \( \frac{1}{4} \).

---

### **Correctness and Complexity**

#### **Correctness**:
- The algorithm guarantees that the expected weight of the cut is \( \frac{1}{4} \) of the optimal solution.
- Random assignment ensures uniform probability distribution, maintaining fairness.

#### **Complexity**:
1. **Random Assignment**:
   - Assigning \( n \) vertices to subsets \( U \) and \( W \) takes \( O(n) \).
2. **Weight Calculation**:
   - Iterating through \( m \) arcs to compute the cut weight takes \( O(m) \).
3. **Total Time Complexity**:
   - \( O(n + m) \), linear in the size of the graph.

---

### **Example**

#### **Graph**:
- Vertices: \( V = \{A, B, C, D\} \).
- Arcs and Weights:
  \[
  A = \{(A, B, 3), (B, C, 2), (C, D, 4), (D, A, 1)\}.
  \]

#### **Random Partitioning**:
- Assign:
  - \( A \to U \), \( B \to W \), \( C \to U \), \( D \to W \).

#### **Cut Calculation**:
- Arcs contributing to the cut:
  - \( (A, B) \): \( A \in U, B \in W \), weight = 3.
  - \( (C, D) \): \( C \in U, D \in W \), weight = 4.
- Total cut weight = \( 3 + 4 = 7 \).

---

### **Relevant Lecture Content**
- **Directed Graph Cuts**:
  - Partitioning directed graphs to optimize specific metrics.
- **Randomized Approximation Algorithms**:
  - Use of probabilistic methods to approximate optimal solutions.
  - Application of independence and expected value analysis.

---
