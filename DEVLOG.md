# Development Log – The Torchbearer

**Student Name:** Zhongyu Hu
**Student ID:** 134165574

---

## Entry 1 – [05/10/2026]: Initial Plan

This problem is finding a path that starts from S, visits all relics, and ends at T with minimum total cost. The key is not just finding a shortest path, but an optimal collection order and path. I plan to first compute the shortest distances between every nodes, then try different orders to find the optimal path. To test my code, I will use new graphs to verify correctness.

---

## Entry 2 – [05/13/2026]: Dijkstra Bug Fix

In `run_dijkstra()` programming, I referred to the example code provided in the assignment and GeeksforGeeks, but I made a mistake in the priority queue implementation. I used `(node, distance)` to store, which would not pop the node with the minimum distance because the `heapq` in Python sorts based on the first element of the tuple. I resolved it by changing to `(distance, node)`. This was a crucial fix for the Dijkstra's algorithm function.

---

## Entry 3 – [Date]: [Short description]

_Your entry here._

---

## Entry 4 – [5/13/2026]: Post-Implementation Reflection

Given more time, I would implement a more efficient search algorithm for finding the optimal order of visiting relics. Additionally, I would add more test cases, like edge cases with varying graph structures and numbers of relics.

---

## Final Entry – [Date]: Time Estimate

| Part | Estimated Hours |
|---|---|
| Part 1: Problem Analysis | 0.5 |
| Part 2: Precomputation Design | 0.5 + 1 |
| Part 3: Algorithm Correctness | 1 |
| Part 4: Search Design | 0.5 |
| Part 5: State and Search Space | 1 + 1 |
| Part 6: Pruning | 1 + 0.5 |
| Part 7: Implementation | 0.5 |
| README and DEVLOG writing | 1 for DEVLOG totally |
| **Total** | 8.5 |
