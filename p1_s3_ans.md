### Detailed Solution for Problem S-3: Finding Maximal Points in the Plane

---

#### **Problem Restatement**
Given a set of \( n \) points \( P = \{(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\} \) in the Euclidean plane:
1. A point \( (x_i, y_i) \) dominates another point \( (x_j, y_j) \) if \( x_i > x_j \) and \( y_i > y_j \).
2. A **maximal point** is not dominated by any other point.

Develop and analyze the **Kirkpatrick-Seidel algorithm** to find all maximal points.

---

### **3.a Correctness of the Algorithm**
#### **Algorithm Description**
1. **Divide and Conquer**:
   - Divide \( P \) into two halves, \( P_\ell \) (points with \( x \)-coordinate ≤ median) and \( P_r \) (points with \( x \)-coordinate > median).
2. **Find Local Maximal Points**:
   - Identify the highest \( y \)-coordinate point \( q \) in \( P_r \). It is guaranteed to be a maximal point.
   - Remove all points in \( P_\ell \) and \( P_r \) dominated by \( q \).
3. **Recursive Calls**:
   - Recursively find maximal points in \( P_\ell \) and \( P_r \).
4. **Combine Results**:
   - The final set of maximal points is the union of maximal points from \( P_\ell \), \( P_r \), and \( \{q\} \).

---

#### **Correctness Proof**
1. **Base Cases**:
   - If \( P = \emptyset \): Return \( \emptyset \) (trivially correct).
   - If \( |P| = 1 \): The single point is maximal (no other points to dominate it).

2. **Maximality of \( q \)**:
   - The highest \( y \)-coordinate point in \( P_r \) cannot be dominated because all other points in \( P_r \) have smaller \( y \)-coordinates.

3. **Pruning**:
   - Removing points dominated by \( q \) ensures that:
     - Only potential maximal points remain for recursive processing.
     - No point dominated by \( q \) will incorrectly appear in the output.

4. **Combination**:
   - Maximal points from \( P_\ell \), \( P_r \), and \( \{q\} \) are combined. Since points are pruned at each level, the algorithm guarantees correctness.

---

### **3.b Time Complexity of \( O(n \log n) \)**
#### **Analysis**
1. **Divide Step**:
   - Computing the median \( x \)-coordinate takes \( O(n) \) using a linear-time median-finding algorithm.
   - Splitting \( P \) into \( P_\ell \) and \( P_r \) takes \( O(n) \).

2. **Dominance Check**:
   - Identifying the maximal point \( q \) in \( P_r \) and removing dominated points takes \( O(n) \).

3. **Recursive Relation**:
   - \( T(n) = 2T(n/2) + O(n) \).

4. **Solution**:
   - Using the Master Theorem, \( T(n) = O(n \log n) \).

---

### **3.c Time Complexity of \( O(n \log h) \)**
#### **Observation**
- Let \( h \) be the number of maximal points.
- Not all recursive calls are balanced:
  - Points dominated by \( q \) are removed entirely, potentially leaving \( O(h) \) points in some branches.

#### **Analysis**
1. **Dominance Reduces Work**:
   - For every maximal point \( q \), a significant number of dominated points are removed.

2. **Parameterized Recursion**:
   - \( T(n) = T(n - h) + O(h \log h) \), where \( h \) is the number of maximal points.
   - Work scales with the logarithm of \( h \) rather than \( n \).

3. **Final Complexity**:
   - \( T(n) = O(n \log h) \), as the recursion depth depends on \( h \), not \( n \).

---

### **Example**
#### **Input**:
Points \( P = \{(1, 2), (3, 1), (2, 4), (5, 3), (4, 6)\} \).

#### **Steps**:
1. Compute Median \( x \)-coordinate:
   - Median \( x = 3 \).
   - \( P_\ell = \{(1, 2), (2, 4), (3, 1)\} \), \( P_r = \{(4, 6), (5, 3)\} \).

2. Process \( P_r \):
   - \( q = (4, 6) \) (highest \( y \)-coordinate in \( P_r \)).
   - Remove points dominated by \( q \) in \( P_\ell \): \( \{(2, 4)\} \).

3. Recursive Calls:
   - \( P_\ell = \{(1, 2), (2, 4)\} \): Find \( (2, 4) \) as maximal.
   - Combine results.

4. **Output**:
   - Maximal points: \( \{(2, 4), (4, 6), (5, 3)\} \).

---

### **Conclusion**
- **Algorithm**: Divide and conquer via Kirkpatrick-Seidel method.
- **Correctness**: Proven via pruning and recursive logic.
- **Time Complexity**:
  - \( O(n \log n) \) for standard cases.
  - \( O(n \log h) \) when \( h \) maximal points dominate the recursion.

