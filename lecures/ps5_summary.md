### Summary of Solutions for Problem Set 5

---

#### **Question 1: Minimum (s, t)-Cut with the Fewest Edges**
**Problem**: Design an efficient algorithm to find the minimum (s, t)-cut in a flow network \( G \) that minimizes the number of edges among all possible minimum cuts.

**Solution**:
1. **Algorithm**:
   - Find the maximum flow using any standard algorithm (e.g., Ford-Fulkerson or Edmonds-Karp).
   - Compute the residual graph.
   - Perform a BFS or DFS from \( s \) in the residual graph to identify reachable vertices.
   - Identify edges crossing from reachable to non-reachable vertices as part of the minimum cut.
   - Among all minimum cuts, select the one with the fewest edges by iterating over reachable components.

**Relevant Lecture**:
- **Network Flow**:
  - Max-flow min-cut theorem.
  - BFS/DFS for identifying cuts in residual graphs.

---

#### **Question 2: Determining Unique Max-Flow and Min-Cut**
**Problem**: Determine whether:
1. (a) The given network contains a unique max-flow.
2. (b) The given network contains a unique minimum (s, t)-cut.

**Solution**:
1. **(a) Unique Max-Flow**:
   - A max-flow is unique if and only if no augmenting paths exist in the residual graph after computing the max-flow.

2. **(b) Unique Minimum Cut**:
   - A minimum cut is unique if and only if there is no alternative set of edges yielding the same minimum cut value.

**Relevant Lecture**:
- **Network Flow**:
  - Residual graphs and augmenting paths for flow uniqueness.
  - Minimum cut uniqueness conditions.

---

#### **Question 3: Minimum Cut Edge Directionality**
**Problem**: Let \( (u, v) \) be an edge in \( G \). Prove that if there is a minimum (s, t)-cut \( (S, T) \) such that \( u \in S \) and \( v \in T \), then no minimum (s, t)-cut \( (S', T') \) exists where \( u \in T' \) and \( v \in S' \).

**Solution**:
1. **Proof**:
   - Use the Max-Flow Min-Cut theorem to show that switching the directionality of \( u \) and \( v \) in a minimum cut would contradict the conservation of flow across the cut.

**Relevant Lecture**:
- **Flow Conservation**:
  - Relationship between edge directionality and cuts.

---

#### **Question 4: Menger’s Theorem**
**Problem**: Prove Menger’s Theorem:
- In an undirected graph \( G \), the size of the minimum vertex cut separating two non-adjacent vertices \( x \) and \( y \) equals the maximum number of pairwise internally disjoint paths between \( x \) and \( y \).

**Solution**:
1. **Proof Outline**:
   - Convert the graph into a flow network by:
     - Treating edges as capacity-1.
     - Using \( x \) as the source and \( y \) as the sink.
   - Apply the Max-Flow Min-Cut theorem to show that the size of the minimum vertex cut matches the maximum flow, which corresponds to the maximum number of disjoint paths.

**Relevant Lecture**:
- **Max-Flow Min-Cut Theorem**:
  - Applications in path disjointness and vertex cuts.

---

### Summary of Relevant Lecture Topics
1. **Network Flow Algorithms**:
   - Max-flow min-cut theorem.
   - Residual graph construction and analysis.
2. **Graph Theory**:
   - Vertex and edge cuts.
   - Internally disjoint paths and connectivity. 
