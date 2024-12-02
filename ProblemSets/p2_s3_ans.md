### Full Solution for Problem 3: Maximizing Museum Attendance

---

#### **Problem Restatement**
A museum can admit up to \( n \) people per day, but visitors arrive in groups. Each group \( g_i \) must either be fully admitted or fully rejected. The goal is to maximize the number of admitted people.

---

### **Solution for 3.a: Greedy Algorithm as a 2-Approximation**
#### **Algorithm: GroupAdmission**
1. **Sort** groups \( G = \{g_1, g_2, \dots, g_m\} \) by size in descending order.
2. Initialize:
   - \( \text{remaining} \leftarrow n \).
   - \( \text{admitted} \leftarrow 0 \).
3. For each group \( g_i \):
   - If \( g_i \leq \text{remaining} \), admit the group:
     \[
     \text{remaining} \leftarrow \text{remaining} - g_i, \quad \text{admitted} \leftarrow \text{admitted} + g_i.
     \]
   - Otherwise, reject the group.

#### **Proof of 2-Approximation**:
1. **Optimal Solution (\( OPT \))**:
   - Admits the maximum number of people \( \leq n \).
2. **Greedy Solution (\( GREEDY \))**:
   - Admits the largest groups first until the remaining capacity is insufficient.
3. **Key Observation**:
   - Any group \( g_i \) skipped by \( GREEDY \) exceeds the remaining capacity.
   - At most one group \( g_{OPT} \) admitted by \( OPT \) can replace \( GREEDY \)’s selected groups, and the size of \( g_{OPT} \) is bounded by \( n \).
4. **Approximation Ratio**:
   \[
   GREEDY \geq \frac{OPT}{2}.
   \]

---

### **Solution for 3.b: Counterexample for Greedy Algorithm**
#### **Objective**:
Provide an example where \( GREEDY \) achieves only half the optimal attendance.

#### **Example**:
- Museum capacity: \( n = 100 \).
- Groups:
  \[
  G = \{99, 98, 2, 2, 2, \dots, 2 \} \quad (\text{50 groups of size 2}).
  \]
- **Greedy Admission**:
  - Admits \( 99 \), leaving \( 1 \) capacity.
  - Total attendance: \( 99 \).
- **Optimal Admission**:
  - Admits \( 2, 2, 2, \dots, 2 \) (50 groups of size 2).
  - Total attendance: \( 100 \).
- **Ratio**:
  \[
  \frac{GREEDY}{OPT} = \frac{99}{100} \to \frac{1}{2} \text{ as \( n \to \infty \)}.
  \]

---

### **Solution for 3.c: Space-Efficient Algorithm**
#### **Objective**:
Provide a 2-approximation algorithm using \( O(1) \) space and \( O(m) \) or \( O(m \log n) \) time.

#### **Approach 1: Two-Pass Algorithm**
1. **First Pass**:
   - Calculate the total sum of all group sizes \( \text{Sum}(G) \).
   - Identify groups \( g_i \) where \( g_i \leq n \) (admissible groups).
2. **Second Pass**:
   - Process each admissible group sequentially, admitting as many as possible without exceeding \( n \).
3. **Implementation**:
   - Use two counters:
     - \( \text{remaining} \): Tracks remaining capacity.
     - \( \text{admitted} \): Tracks total admitted people.

#### **Time Complexity**:
- **First Pass**: \( O(m) \) to compute \( \text{Sum}(G) \).
- **Second Pass**: \( O(m) \) to admit or reject groups.
- Total: \( O(m) \).

---

### **Alternative Approach: Bucket Sort for \( O(m \log n) \)**
1. **Idea**:
   - Use bucket sort to group sizes \( g_i \) into buckets based on their value.
   - This avoids full sorting but retains order for efficient admission.
2. **Steps**:
   - Create buckets for group sizes.
   - Process buckets from largest to smallest.
   - Admit groups from the largest available bucket until \( n \) is exhausted.

#### **Time Complexity**:
- Bucket sort: \( O(m \log n) \).
- Admission step: \( O(m) \).
- Total: \( O(m \log n) \).

---

### **Conclusion**
- **3.a**: Greedy algorithm is a simple 2-approximation that prioritizes largest groups first.
- **3.b**: Greedy can fail by leaving small unused capacity, achieving only \( 1/2 \) of the optimal.
- **3.c**: Space-efficient algorithms use either a two-pass approach (\( O(m) \)) or bucket sorting (\( O(m \log n) \)) to achieve similar results.
