### Summary of Problem Set 3 Solutions and Relevant Lecture Contents

---

#### **Problem 1: Maximum \( k \)-Cut Problem**

**Question**: 
Partition the vertex set \( V \) of a weighted graph \( G = (V, E) \) into \( k \) parts to maximize the total weight of edges whose endpoints are in different parts. Provide a randomized \( \frac{k-1}{k} \)-approximation algorithm.

---

**Solution**:
1. **Algorithm**:
   - Assign each vertex \( v \in V \) to one of \( k \) partitions uniformly at random.
   - For each edge \( (i, j) \in E \):
     - If \( i \) and \( j \) are in different partitions, include the edge's weight \( w_{ij} \) in the total.

2. **Expected Performance**:
   - For a randomly chosen partitioning:
     - Each edge has a probability of \( \frac{k-1}{k} \) of being cut.
   - Expected weight of the cut is \( \frac{k-1}{k} \cdot \text{OPT} \), where \( \text{OPT} \) is the maximum weight.

3. **Approximation Ratio**:
   - The randomized algorithm achieves an approximation factor of \( \frac{k-1}{k} \).

---

**Relevant Lecture Content**:
- **Lecture on Randomized Approximation Algorithms**:
  - Concepts of probabilistic guarantees in optimization.
  - Application of random assignments in partitioning problems.

---

#### **Problem 2: Maximum Directed Cut (MAX DI-CUT)**

**Question**:
Partition the vertices of a directed graph \( G = (V, A) \) into two sets \( U \) and \( W = V - U \) to maximize the total weight of arcs going from \( U \) to \( W \). Provide a randomized \( \frac{1}{4} \)-approximation algorithm.

---

**Solution**:
1. **Algorithm**:
   - Assign each vertex \( v \) to \( U \) or \( W \) uniformly at random.
   - For each arc \( (i, j) \in A \):
     - If \( i \in U \) and \( j \in W \), include the arc's weight \( w_{ij} \) in the total.

2. **Expected Performance**:
   - Each directed arc \( (i, j) \) contributes to the cut with a probability of \( \frac{1}{4} \) (due to independent random assignment of \( i \) and \( j \)).
   - Expected weight of the cut is \( \frac{1}{4} \cdot \text{OPT} \).

3. **Approximation Ratio**:
   - The randomized algorithm achieves an approximation factor of \( \frac{1}{4} \).

---

**Relevant Lecture Content**:
- **Lecture on Partitioning and Directed Graph Problems**:
  - Randomized strategies for directed graph cuts.
  - Use of independence in vertex assignments.

---

#### **Problem 3: Integer Programming and LP Relaxation for MAX DI-CUT**

**Question**:
1. Formulate the maximum directed cut problem as an integer program.
2. Use randomized rounding on the LP relaxation to achieve a \( \frac{1}{2} \)-approximation.

---

**Solution**:
1. **Integer Programming Formulation**:
   - Define variables:
     - \( x_i \in \{0, 1\} \): \( 1 \) if vertex \( i \) is in \( U \), \( 0 \) otherwise.
     - \( z_{ij} \in \{0, 1\} \): \( 1 \) if \( (i, j) \) is included in the cut.
   - Objective:
     \[
     \text{Maximize } \sum_{(i, j) \in A} w_{ij} z_{ij}
     \]
   - Constraints:
     \[
     z_{ij} \leq x_i, \quad z_{ij} \leq 1 - x_j, \quad 0 \leq z_{ij} \leq 1.
     \]

2. **Randomized Rounding Algorithm**:
   - Solve the LP relaxation (allowing \( x_i, z_{ij} \in [0, 1] \)).
   - Assign each vertex \( i \) to \( U \) with probability \( \frac{1}{4} + \frac{x_i}{2} \).
   - For each arc \( (i, j) \):
     - Compute the contribution based on rounded values of \( x_i \) and \( x_j \).

3. **Approximation Analysis**:
   - Each directed arc contributes to the cut with a probability proportional to \( \frac{x_i (1 - x_j)}{2} \).
   - The expected weight of the cut is \( \frac{1}{2} \cdot \text{OPT} \).

---

**Relevant Lecture Content**:
- **Lecture on LP Relaxations and Rounding**:
  - Integer programming models for graph problems.
  - Randomized rounding techniques to approximate optimal solutions.

---

### Summary of Lecture Connections
- **Problem 1**: Lecture on Randomized Approximation Algorithms for Partitioning Problems.
- **Problem 2**: Lecture on Directed Graph Cuts and Independence in Assignments.
- **Problem 3**: Lecture on LP Relaxation, Integer Programming, and Randomized Rounding Techniques.
