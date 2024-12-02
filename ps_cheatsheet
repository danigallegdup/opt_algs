### Cheatsheet for 18 Problems

---

### **Problem Set 1**
1. **Minimum (s, t)-Cut with Fewest Edges**:
   - **Goal**: Minimize edges among all minimum cuts.
   - **Steps**:
     1. Compute max-flow.
     2. Identify reachable vertices from \( s \) in the residual graph.
     3. Select edges crossing from reachable to non-reachable vertices.
     4. Optimize for fewest edges.
   - **Key Concept**: Max-flow min-cut theorem.

2. **Unique Max-Flow**:
   - **Condition**: No augmenting paths in the residual graph.
   - **Steps**:
     1. Compute max-flow.
     2. Check for augmenting paths in the residual graph.
   - **Key Concept**: Augmenting paths.

3. **Unique Minimum Cut**:
   - **Condition**: Only one way to partition \( V \) into \( S \) and \( T \) with the same capacity.
   - **Steps**:
     1. Compute max-flow and residual graph.
     2. Verify if multiple partitions yield the same cut capacity.
   - **Key Concept**: Uniqueness of cuts in residual graphs.

---

### **Problem Set 2**
4. **Minimum Cut Edge Directionality**:
   - **Statement**: If \( u \in S, v \in T \) in one minimum cut, the reverse \( u \in T, v \in S \) is impossible.
   - **Proof**:
     - Reversing edge direction violates flow conservation or increases cut capacity.
   - **Key Concept**: Max-flow min-cut theorem and residual capacity.

5. **Menger’s Theorem**:
   - **Statement**: Size of the minimum vertex cut = Maximum number of disjoint \( s \)-\( t \) paths.
   - **Steps**:
     1. Convert graph to a flow network with unit capacities.
     2. Compute max-flow and apply the min-cut theorem.
   - **Key Concept**: Relationship between paths and cuts.

---

### **Problem Set 3**
6. **Maximum \( k \)-Cut Problem**:
   - **Goal**: Partition \( V \) into \( k \) subsets to maximize cut edge weight.
   - **Algorithm**:
     - Assign each vertex to a random subset.
     - Approximation ratio: \( \frac{k-1}{k} \).
   - **Key Concept**: Randomized approximation.

7. **Maximum Directed Cut (MAX DI-CUT)**:
   - **Goal**: Partition \( V \) into two subsets to maximize directed cut edge weight.
   - **Algorithm**:
     - Randomly assign vertices to subsets \( U, W \).
     - Approximation ratio: \( \frac{1}{4} \).
   - **Key Concept**: Randomized assignment.

8. **MAX DI-CUT with LP Relaxation**:
   - **Goal**: Improve approximation using LP relaxation and randomized rounding.
   - **Steps**:
     1. Formulate LP.
     2. Use fractional solutions to guide randomized assignments.
     - Approximation ratio: \( \frac{1}{2} \).
   - **Key Concept**: LP relaxation and rounding.

---

### **Problem Set 4**
9. **Lovász Local Lemma (LLL)**:
   - **Symmetric Form**:
     - If \( P(A_i) \leq p \) and \( ep(d+1) \leq 1 \), then \( A_i \) can be avoided.
   - **Key Concept**: Probabilistic event dependencies.

10. **Edge Coloring of \( K_n \)**:
    - **Goal**: Ensure no monochromatic \( K_k \) in 2-coloring.
    - **Key Inequality**:
      \[
      4 \binom{k}{2} \binom{n-2}{k-2} 2^{1-\binom{k}{2}} \leq 1.
      \]
    - **Key Concept**: Probabilistic method.

11. **Hypergraph 2-Colorability**:
    - **(a)** Uniform hypergraphs: \( \Delta \leq \frac{2^{k-3}}{k-1} \).
    - **(b)** Regular hypergraphs: \( k \geq 9 \).
    - **(c)** Non-uniform hypergraphs: Sum of dependency terms \( \leq \frac{1}{8} \).
    - **Key Concept**: Lovász Local Lemma.

12. **Independent Sets in Graphs**:
    - **Goal**: Find an independent set with one vertex from each \( V_i \).
    - **Key Concept**: Random selection and LLL.

---

### **Problem Set 5**
13. **Kőnig’s Theorem**:
    - **Statement**: Size of max matching = Size of min vertex cover in bipartite graphs.
    - **Proof**:
      - Use max-flow min-cut theorem to relate matching and covering.
    - **Key Concept**: Duality in bipartite graphs.

14. **Disrupting Maximum Flow with Edge Deletion**:
    - **Goal**: Minimize max-flow by deleting \( k \) edges.
    - **Algorithm**:
      - Target edges in the minimum cut.
    - **Key Concept**: Max-flow reduction.

15. **Detecting Cycle Covers**:
    - **Goal**: Determine if a directed graph has a cycle cover.
    - **Algorithm**:
      - Convert to bipartite graph and check for a perfect matching.
    - **Key Concept**: Matchings and cycle equivalence.

---

### **Problem Set 6**
16. **Vertex Cover in Weighted Graphs**:
    - **Goal**: Find minimum weight vertex cover.
    - **Algorithm**:
      - Formulate as LP and use rounding.
    - **Key Concept**: LP rounding for covering problems.

17. **Edge Cover in Graphs**:
    - **Goal**: Find minimum weight edge cover.
    - **Algorithm**:
      - Solve weighted matching and construct the cover.
    - **Key Concept**: Matching for edge covers.

18. **Feedback Vertex Set**:
    - **Goal**: Remove vertices to break all cycles in a graph.
    - **Algorithm**:
      - Use iterative removal or approximate algorithms for NP-hard cases.
    - **Key Concept**: Cycle breaking via vertex removal.

---

Let me know if you'd like further elaboration on any specific problem!
