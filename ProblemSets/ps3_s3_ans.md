### Full Solution for Problem 3: Integer Programming and LP Relaxation for MAX DI-CUT

---

#### **Problem Restatement**
1. Formulate the Maximum Directed Cut (MAX DI-CUT) problem as an integer program.
2. Use randomized rounding on the LP relaxation to achieve a \( \frac{1}{2} \)-approximation.

---

### **Part 1: Integer Programming Formulation**

#### **Variables**:
- Let \( x_i \in \{0, 1\} \):
  - \( x_i = 1 \) if vertex \( i \) is in subset \( U \), and \( x_i = 0 \) if \( i \in W \).
- Define \( z_{ij} \in \{0, 1\} \):
  - \( z_{ij} = 1 \) if the directed arc \( (i, j) \) is in the cut, and \( z_{ij} = 0 \) otherwise.

---

#### **Objective**:
Maximize the total weight of arcs in the cut:
\[
\text{Maximize } \sum_{(i, j) \in A} w_{ij} z_{ij}.
\]

---

#### **Constraints**:
1. \( z_{ij} \leq x_i \) (arc \( (i, j) \) can only be in the cut if \( i \in U \)).
2. \( z_{ij} \leq 1 - x_j \) (arc \( (i, j) \) can only be in the cut if \( j \in W \)).
3. \( z_{ij} \geq x_i - x_j \) (to ensure proper inclusion of arcs based on assignments).
4. \( x_i \in \{0, 1\}, \, z_{ij} \in \{0, 1\} \).

---

### **Part 2: LP Relaxation**

#### **Relaxed Variables**:
- Allow \( x_i, z_{ij} \in [0, 1] \), turning the integer program into a linear program.

#### **Objective**:
Maximize:
\[
\text{Maximize } \sum_{(i, j) \in A} w_{ij} z_{ij}.
\]

#### **Constraints**:
1. \( z_{ij} \leq x_i \).
2. \( z_{ij} \leq 1 - x_j \).
3. \( z_{ij} \geq x_i - x_j \).
4. \( x_i, z_{ij} \in [0, 1] \).

---

### **Part 3: Randomized Rounding**

#### **Algorithm**:
1. **Solve LP Relaxation**:
   - Compute fractional values \( x_i \in [0, 1] \) and \( z_{ij} \in [0, 1] \).
2. **Randomized Assignment**:
   - Assign each vertex \( i \) to \( U \) or \( W \) probabilistically:
     - Assign \( i \in U \) with probability \( x_i \).
     - Assign \( i \in W \) with probability \( 1 - x_i \).
3. **Compute the Cut**:
   - For each arc \( (i, j) \):
     - Include \( (i, j) \) in the cut if \( i \in U \) and \( j \in W \).

---

#### **Analysis of Approximation Factor**

1. **Key Observation**:
   - For each arc \( (i, j) \), the probability of \( i \in U \) and \( j \in W \) is:
     \[
     P(i \in U \text{ and } j \in W) = x_i \cdot (1 - x_j).
     \]
   - This matches the fractional value \( z_{ij} \) from the LP relaxation.

2. **Expected Cut Weight**:
   - The expected weight of the cut is:
     \[
     \mathbb{E}[\text{Cut Weight}] = \sum_{(i, j) \in A} w_{ij} \cdot x_i \cdot (1 - x_j).
     \]
   - This is exactly the LP objective value.

3. **Approximation Factor**:
   - The expected weight of the cut is at least \( \frac{1}{2} \cdot \text{OPT} \), where \( \text{OPT} \) is the optimal value of the integer program.

---

### **Correctness and Complexity**

#### **Correctness**:
- The LP relaxation provides a feasible fractional solution.
- Randomized rounding ensures that each arc contributes to the cut with a probability proportional to its LP value.

#### **Complexity**:
1. **Solving LP**:
   - Standard LP solvers compute the relaxed solution in \( O((n + m)^{3}) \).
2. **Randomized Rounding**:
   - Assigning \( n \) vertices takes \( O(n) \).
   - Calculating the cut weight for \( m \) arcs takes \( O(m) \).
3. **Total Complexity**:
   - \( O((n + m)^3) \), dominated by LP solving.

---

### **Example**

#### **Graph**:
- Vertices: \( V = \{A, B, C\} \).
- Arcs and Weights:
  \[
  A = \{(A, B, 3), (B, C, 5), (C, A, 2)\}.
  \]

#### **LP Solution**:
- Fractional values:
  - \( x_A = 0.7, x_B = 0.4, x_C = 0.6 \).
- \( z_{AB} = 0.7 \cdot (1 - 0.4) = 0.42 \).

#### **Randomized Rounding**:
- Assign vertices probabilistically:
  - \( A \in U \) with probability 0.7.
  - \( B \in U \) with probability 0.4.
  - \( C \in U \) with probability 0.6.

#### **Expected Cut**:
- Arcs in the cut depend on rounded assignments:
  - \( (A, B) \): Contributes with probability \( 0.7 \cdot 0.6 = 0.42 \).

---

### **Relevant Lecture Content**
- **Integer Programming and LP Relaxation**:
  - Modeling combinatorial problems as integer programs.
- **Randomized Rounding**:
  - Probabilistic techniques to convert fractional solutions to feasible integer solutions.

