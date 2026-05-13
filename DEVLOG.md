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

## Entry 4 – [Date]: Post-Implementation Reflection

> Required. Written after your implementation is complete. Describe what you would
> change or improve given more time.

_Your entry here._

---

## Final Entry – [Date]: Time Estimate

> Required. Estimate minutes spent per part. Honesty is expected; accuracy is not graded.

| Part | Estimated Hours |
|---|---|
| Part 1: Problem Analysis | |
| Part 2: Precomputation Design | |
| Part 3: Algorithm Correctness | |
| Part 4: Search Design | |
| Part 5: State and Search Space | |
| Part 6: Pruning | |
| Part 7: Implementation | |
| README and DEVLOG writing | |
| **Total** | |
