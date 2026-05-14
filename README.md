# The Torchbearer

**Student Name:** Zhongyu Hu
**Student ID:** 134165574
**Course:** CS 460 – Algorithms | Spring 2026

---

## Part 1: Problem Analysis

- **Why a single shortest-path run from S is not enough:**
  A single shortest-path from S would not determine the visiting order, but this problem requires visiting all relics in some orders.

- **What decision remains after all inter-location costs are known:**
  The order of visiting relics. After knowing all inter-location costs, it requires to find an optimal order through these relics with minimum cost.

- **Why this requires a search over orders (one sentence):**
  Because it searches the lowest cost order among many possible orders.

---

## Part 2: Precomputation Design

### Part 2a: Source Selection

| Source Node Type | Why it is a source |
|---|---|
| spawn | It is the start node of the path, it requires the shortest distance from entrance to all specific nodes. |
| relic | In order to compute all possible order, it requires the shortest distance from each relic to other relics and exit node. |

### Part 2b: Distance Storage

| Property | Your answer |
|---|---|
| Data structure name | Dictionary |
| What the keys represent | The current node |
| What the values represent | The shortest distance from source node to each current node |
| Lookup time complexity | `O(1)` |
| Why O(1) lookup is possible | Because a hash table allows direct access to values using keys |

### Part 2c: Precomputation Complexity

- **Number of Dijkstra runs:** `k + 1`
- **Cost per run:** Let `n = |V|`, `m = |E|`, `k = |M|`. Single shortest-path run costs `O(m log n)`.
- **Total complexity:** `O((k + 1) * m log n) = O(k * m log n)`
- **Justification (one line):** Since every source node including entrance and all relics requires a Dijkstra run, the total number of runs is `k + 1`, and each run has a complexity of `O(m log n)`, leading to an total complexity of `O(k * m log n)`.

---

## Part 3: Algorithm Correctness

### Part 3a: What the Invariant Means

- **For nodes already finalized (in S):**
  The shortest distance from the source to these nodes is confirmed and always holds true through the iterations.

- **For nodes not yet finalized (not in S):**
  The distance from the source to these nodes is an upper bound of the actual shortest distance, and it might update shorter through the iterations.

### Part 3b: Why Each Phase Holds

- **Initialization : why the invariant holds before iteration 1:**
  Before iteration 1, the set S is empty, so there are no finalized nodes. The distance to the source node itself is 0, which is correct, and the distances to all other nodes are set to infinity, which is an upper bound.

- **Maintenance : why finalizing the min-dist node is always correct:**
  The node comes from the priority queue with the smallest distance, and since all edge weights are non-negative, any path through this node to other nodes cannot be shorter than the already known distance to this node. Therefore, finalizing this node is correct.

- **Termination : what the invariant guarantees when the algorithm ends:**
  When the algorithm ends, all nodes have been finalized, and the shortest distance from the source to every node is confimed.

### Part 3c: Why This Matters for the Route Planner

Dijkstra's algorithm determines the shortest paths from the source to all other nodes, which is essential for the route planner to compute the possible cost of different orders of visiting relics.

---

## Part 4: Search Design

### Why Greedy Fails

- **The failure mode:** The greedy approach always picks the next relic with the lowest immediate cost.

- **Counter-example setup:** 
  
  **Entrance:** S | **Relic chambers:** B, C | **Exit:** T
  
  After computing cheapest inter-location travel costs, suppose you have:

  | From \ To | B   | C   | T   |
  |-----------|-----|-----|-----|
  | S         | 1   | 2   | --  |
  | B         | --  | 100 | 1   |
  | C         | 1   | --  | 100 |

- **What greedy picks:** S -> B -> C -> T &nbsp; total fuel = 1 + 100 + 100 = **201**
- **What optimal picks:** S -> C -> B -> T &nbsp; total fuel = 2 + 1 + 1 = **4**
- **Why greedy loses:** The greedy loses because it only considers the immediate cost to the next relic, which leads to high total cost at the end, while the optimal considers the overall cost of the entire path.  

### What the Algorithm Must Explore

- Different orders of visiting all relics

---

## Part 5: State and Search Space

### Part 5a: State Representation

> Document the three components of your search state as a table.
> Variable names here must match exactly what you use in torchbearer.py.

| Component | Variable name in code | Data type | Description |
|---|---|---|---|
| Current location | | | |
| Relics already collected | | | |
| Fuel cost so far | | | |

### Part 5b: Data Structure for Visited Relics

> Fill in the table.

| Property | Your answer |
|---|---|
| Data structure chosen | |
| Operation: check if relic already collected | Time complexity: |
| Operation: mark a relic as collected | Time complexity: |
| Operation: unmark a relic (backtrack) | Time complexity: |
| Why this structure fits | |

### Part 5c: Worst-Case Search Space

> Two bullets.

- **Worst-case number of orders considered:** _Your answer (in terms of k)._
- **Why:** _One-line justification._

---

## Part 6: Pruning

### Part 6a: Best-So-Far Tracking

> Three bullets.

- **What is tracked:** _Your answer here._
- **When it is used:** _Your answer here._
- **What it allows the algorithm to skip:** _Your answer here._

### Part 6b: Lower Bound Estimation

> Three bullets.

- **What information is available at the current state:** _Your answer here._
- **What the lower bound accounts for:** _Your answer here._
- **Why it never overestimates:** _Your answer here._

### Part 6c: Pruning Correctness

> One to two bullets. Explain why pruning is safe.

- _Your answer here._

---

## References

> Bullet list. If none beyond lecture notes, write that.

- _Your references here._
