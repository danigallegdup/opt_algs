### Full Solution for Problem 2: Eulerian Path and Graph Modifications
---

#### **Problem Restatement**
1. Humperdink and Mildred run two hotels in a tourist town. Guests at their hotels need to traverse all roads exactly once and end at the Central Plaza.
2. Solve three subproblems:
   - **2.a**: Add a road for Humperdink’s hotel to create an Eulerian path starting at his hotel and ending at the Central Plaza.
   - **2.b**: Add a road for Mildred’s hotel to create an Eulerian path for her guests but prevent one for Humperdink’s guests.
   - **2.c**: Prove the conditions under which a multigraph \( G \) has an Eulerian path.

---

### **Solution for 2.a: Adding a Road for Humperdink’s Guests**
#### **Objective**:
Allow Humperdink’s guests to start at his hotel, traverse all roads exactly once, and end at the Central Plaza.

#### **Approach**:
1. **Condition for Eulerian Path**:
   - A graph has an Eulerian path if:
     - It is connected.
     - Exactly two vertices have odd degree (start and end vertices).
2. **Current Problem**:
   - If Humperdink’s hotel and the Central Plaza both have even degrees, no Eulerian path exists.
3. **Solution**:
   - Add a road between Humperdink’s hotel (odd degree) and any other vertex with an odd degree to make them even, leaving the Central Plaza and Humperdink’s hotel as the only odd-degree vertices.

---

### **Solution for 2.b: Adding a Road for Mildred’s Guests**
#### **Objective**:
Enable Mildred’s guests to traverse all roads exactly once but prevent Humperdink’s guests from doing the same.

#### **Approach**:
1. **Separate Mildred’s Path**:
   - Add a road such that the Eulerian path condition is satisfied for Mildred’s hotel and the Central Plaza.
   - Ensure that any odd-degree adjustment for Mildred’s graph creates odd degrees for vertices specific to Humperdink’s graph.

2. **Implementation**:
   - Connect Mildred’s hotel to a vertex that:
     - Has an odd degree in her subgraph.
     - Does not affect the degree conditions for Humperdink’s subgraph.

---

### **Solution for 2.c: Proof of Eulerian Path Conditions**
#### **Statement**:
A connected multigraph \( G \) has an Eulerian path if and only if:
- Exactly two vertices have odd degrees (the start \( s \) and the end \( d \)).
- All other vertices have even degrees.

---

#### **Proof**:
1. **Necessity**:
   - Consider a walk that uses all edges exactly once:
     - At every vertex, each incoming edge must have a corresponding outgoing edge, making the degree even.
     - Exception: The start vertex \( s \) has one more outgoing than incoming edge (odd degree), and the end vertex \( d \) has one more incoming than outgoing edge (odd degree).

2. **Sufficiency**:
   - Assume \( G \) is connected and exactly two vertices have odd degrees:
     - Start at \( s \). At every step, the even-degree condition allows traversal of edges without becoming stuck.
     - End at \( d \), where the last edge completes the walk.

3. **Conclusion**:
   - The odd-degree vertices are exactly the start and end points of an Eulerian path.
   - If more than two vertices have odd degree, it is impossible to form a path.

---

### **Conclusion**
- **2.a**: Add a road connecting Humperdink’s hotel to an odd-degree vertex, ensuring only his hotel and the Central Plaza have odd degrees.
- **2.b**: Add a road for Mildred’s graph that adjusts odd-degree vertices in her subgraph while leaving Humperdink’s graph non-Eulerian.
- **2.c**: Proven that Eulerian paths require two odd-degree vertices and connectedness.

