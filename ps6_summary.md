### Summary of Problem Set 6 Solutions

---

#### **Question 1: Proof of Kőnig’s Theorem**
**Problem**:
Prove Kőnig’s Theorem, which states that for any bipartite graph:
\[
| \text{Minimum Vertex Cover} | = | \text{Maximum Matching} |.
\]

**Solution**:
1. **Convert to Flow Network**:
   - Treat the bipartite graph \( G = (U \cup V, E) \) as a flow network with:
     - Source \( s \) connected to all \( U \) vertices,
     - Sink \( t \) connected to all \( V \) vertices,
     - Each edge having capacity 1.

2. **Compute Max Flow**:
   - Use a max-flow algorithm to find the maximum flow from \( s \) to \( t \).

3. **Max-Flow Min-Cut Theorem**:
   - The size of the maximum matching is equal to the value of the max-flow.
   - A minimum vertex cover corresponds to a minimum \( s \)-\( t \) cut in the flow network, ensuring \( | \text{Minimum Vertex Cover} | = | \text{Maximum Matching} | \).

**Relevant Lecture**:
- Max-Flow Min-Cut theorem applied to bipartite graphs.

---

#### **Question 2: Disrupting Maximum Flow with Edge Deletion**
**Problem**:
Given a flow network \( G = (V, E) \) with edge capacities of 1, find a set of exactly \( k \) edges to delete such that the maximum flow is minimized.

**Solution**:
1. **Construct the Flow Network**:
   - Treat \( G \) as a flow network with uniform capacity edges.

2. **Edge Selection**:
   - Use the Ford-Fulkerson or Edmonds-Karp algorithm to compute the maximum flow and identify the critical edges in the residual graph.
   - Select \( k \) edges crossing the minimum cut to disrupt the maximum flow optimally.

3. **Correctness Proof**:
   - Removing edges from the minimum cut directly reduces flow capacity in the network.

**Relevant Lecture**:
- Max-flow algorithms and minimum cut strategies for network optimization.

---

#### **Question 3: Detecting Cycle Covers**
**Problem**:
Design an algorithm to determine whether a directed graph \( G \) has a cycle cover (a set of vertex-disjoint cycles covering all vertices). If it exists, find the cycle cover.

**Solution**:
1. **Formulate as a Bipartite Graph**:
   - Construct a bipartite graph \( G' \) where each vertex \( v \in V(G) \) has two copies in \( G' \), and directed edges from \( G \) connect these copies.

2. **Check for Perfect Matching**:
   - A perfect matching in \( G' \) corresponds to a cycle cover in \( G \).

3. **Find the Cycle Cover**:
   - Use a maximum matching algorithm to determine if a perfect matching exists.
   - Construct cycles based on the matching.

**Relevant Lecture**:
- Perfect matchings in bipartite graphs and their applications in cycle detection.

---

### Summary of Relevant Lecture Topics
1. **Max-Flow Min-Cut Theorem**:
   - Applications in bipartite graphs and edge deletion.
2. **Matching Algorithms**:
   - Perfect matchings and their connection to cycle covers.
3. **Network Optimization**:
   - Disruption strategies for minimizing flow.

Let me know if you'd like detailed proofs or algorithm descriptions for any question!
