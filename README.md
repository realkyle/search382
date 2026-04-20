# Search

Pacman search algorithms implemented in Python. The agent finds paths through maze worlds using DFS, BFS, UCS, and A*, then applies these to more complex problems like visiting all corners and eating all food.

## Files Modified

- **search.py** — Search algorithm implementations (Q1–Q4)
- **searchAgents.py** — Search problem definitions and heuristics (Q5–Q8)

## Questions Completed

| Q | Topic | Score |
|---|-------|-------|
| 1 | Depth First Search | 3/3 |
| 2 | Breadth First Search | 3/3 |
| 3 | Uniform Cost Search | 3/3 |
| 4 | A* Search | 3/3 |
| 5 | Corners Problem | 3/3 |
| 6 | Corners Heuristic | 3/3 |
| 7 | Food Heuristic | 5/4 (extra credit) |
| 8 | Suboptimal Search | 3/3 |
| | **Total** | **26/25** |

## Running the Autograder

```
python3 autograder.py
```

To test a specific question:
```
python3 autograder.py -q q1
```

## Key Design Decisions

- **State representation (Q5):** `(position, visited_corners)` — a tuple of 4 booleans, compact and hashable.
- **Corners heuristic (Q6):** Greedy nearest-neighbor with Manhattan distance — 692 nodes expanded.
- **Food heuristic (Q7):** Maze distance to the farthest food, cached per position pair — 4137 nodes expanded (extra credit threshold: ≤7000).
