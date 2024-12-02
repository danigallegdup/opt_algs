### Optimization Algorithms

---

#### **Lecture 1: Introduction**
- Overview of optimization problems.
- Classification:
  - Discrete, Continuous, and Combinatorial Optimization.
- Examples:
  - Shortest Path, Minimum Spanning Tree, Vertex Cover, and TSP.
- Goals of algorithm design:
  - Efficiency, correctness, and complexity analysis.

---

#### **Lecture 2: Linear Programming (LP) Basics**
- Definition and formulation of LP.
- Feasibility and optimization problems.
- LP example: Weighted Vertex Cover.
- Introduction to approximation algorithms:
  - \( 2 \)-approximation for Vertex Cover.
- Greedy algorithms for Set Cover.

---

#### **Lecture 3: Traveling Salesman Problem (TSP)**
- Variants:
  - Metric vs. General, With/Without Repeats.
- Approximation algorithms:
  - 2-Approximation using MST and DFS.
  - Christofides Algorithm (1.5-Approximation).
- Use of triangle inequality for guarantees.

---

#### **Lecture 4: CNF-SAT and Approximation**
- Definition of CNF-SAT:
  - Satisfiability of clauses in conjunctive normal form.
- Randomized algorithms for Weighted k-CNF-SAT:
  - \( (1 - \frac{1}{2^k}) \)-approximation.
- Linear Programming formulation for CNF-SAT.

---

#### **Lecture 5: Lovász Local Lemma (LLL)**
- Probabilistic method for sparse CSPs.
- Application:
  - (d, k)-CSP satisfiability.
- Algorithms leveraging LLL:
  - Moser’s Algorithm for finding solutions efficiently.

---

#### **Lecture 6: Network Flow Basics**
- Flow networks:
  - Definitions of flow, capacity, and conservation constraints.
- Max-Flow Min-Cut Theorem:
  - Equivalence of maximum flow and minimum cut.
- Algorithms:
  - Ford-Fulkerson method for augmenting paths.

---

#### **Lecture 7: Advanced Network Flow Algorithms**
- Improvements to basic max-flow algorithms:
  - Edmonds-Karp: BFS-based augmenting paths.
  - Dinitz Algorithm: Layered network approach.
- Applications:
  - Edge-disjoint paths and vertex-disjoint paths.

---

#### **Lecture 8: Network Flow Applications**
- Bipartite matching via flow networks.
- Vertex capacities:
  - Modifications to account for vertex constraints.
- Path covers in acyclic directed graphs:
  - Minimizing teaching staff in scheduling problems.

---

#### **Lecture 9: Semidefinite Programming (SDP)**
- Introduction to SDP:
  - Extends LP with matrix and semidefinite constraints.
- MaxCut problem:
  - SDP relaxation achieves \( 0.878 \)-approximation.
- Rounding techniques:
  - Hyperplane rounding for vector solutions.

---

#### **Lecture 10: Linear Programming in NP and co-NP**
- Complexity analysis:
  - LP belongs to \( \text{NP} \cap \text{co-NP} \).
- Farkas’ Lemma:
  - Conditions for infeasibility in LP.
- Feasibility and bounded/unbounded regions:
  - Use of box constraints.

---

#### **Lecture 11: Ellipsoid Method**
- Polynomial-time algorithm for LP feasibility.
- Key concepts:
  - Volume reduction, separating hyperplanes.
- Applications of LP duality:
  - Max-Flow Min-Cut equivalence and bipartite matching.

