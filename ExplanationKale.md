# Search Assignment — Code Changes Overview

## search.py

All four search functions follow the same pattern: maintain a fringe, a visited set, and track the path of actions to each state.

**depthFirstSearch** (lines 89–104) — Uses `util.Stack` (LIFO). Pops the most recently added node first, diving deep before backtracking. Does not guarantee shortest path.

**breadthFirstSearch** (lines 108–123) — Uses `util.Queue` (FIFO). Explores all nodes at depth N before depth N+1, guaranteeing the fewest-actions path.

**uniformCostSearch** (lines 127–143) — Uses `util.PriorityQueue` keyed on cumulative path cost `g(n)`. Expands the cheapest node first, guaranteeing the least-cost path even when step costs vary.

**aStarSearch** (lines 154–171) — Uses `util.PriorityQueue` keyed on `g(n) + h(n)` (cost so far + heuristic estimate). With an admissible/consistent heuristic, finds the optimal path while expanding fewer nodes than UCS.

---

## searchAgents.py

**CornersProblem.__init__** (lines 288–289) — Computes the initial visited-corners tuple by checking if the starting position matches any of the four corners, and stores it as `self.startState`.

**CornersProblem.getStartState** (lines 291–296) — Returns `self.startState`, the `(position, visited_corners)` tuple set up in `__init__`.

**CornersProblem.isGoalState** (lines 298–302) — Returns `True` when all four booleans in `state[1]` are `True`, meaning every corner has been visited.

**CornersProblem.getSuccessors** (lines 315–323) — Moves to adjacent non-wall positions and updates the visited-corners tuple by OR-ing each boolean with whether the new position matches that corner.

**cornersHeuristic** (lines 358–371) — Greedy nearest-neighbor over unvisited corners using Manhattan distance. From the current position, repeatedly picks the closest unvisited corner and sums the distances. Admissible (Manhattan ≤ actual maze distance) and consistent (triangle inequality). Expands 692 nodes on mediumCorners.

**foodHeuristic** (lines 463–479) — Uses actual maze distance (BFS) to the farthest remaining food pellet. Results are cached in `problem.heuristicInfo['dist_cache']` so each pair of positions is only computed once. Admissible because Pacman must reach the farthest food at minimum. Consistent because maze distance changes by at most 1 per step. Expands 4137 nodes on trickySearch (extra credit threshold: ≤7000).

**findPathToClosestDot** (line 509) — Solves `AnyFoodSearchProblem` with `search.bfs`, returning the shortest path to the nearest food pellet. Called repeatedly by `ClosestDotSearchAgent` to greedily eat the closest dot at each step.

**AnyFoodSearchProblem.isGoalState** (lines 537–543) — Returns `True` if the current position `(x, y)` has food: `self.food[x][y]`.
