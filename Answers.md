# Search Assignment Answers

## Question 1: Depth First Search

Implemented `depthFirstSearch` in `search.py` using `util.Stack` for LIFO ordering. Each fringe entry stores `(state, actions)` so the path can be reconstructed. A `visited` set prevents re-expanding already-seen states (graph search). Successors are pushed in the order returned by `getSuccessors`, yielding a 130-step solution on mediumMaze.

## Question 8: Suboptimal Search

Implemented `AnyFoodSearchProblem.isGoalState` to return `True` when the current position contains food (`self.food[x][y]`). Implemented `findPathToClosestDot` by solving that problem with `search.bfs`, which finds the shortest path to the nearest food. This is suboptimal overall because greedily going to the nearest dot can force backtracking across the maze — a small detour now might avoid a long one later.

## Question 7: Eating All the Dots Heuristic

Implemented `foodHeuristic` using the maze distance to the farthest remaining food pellet, with results cached in `problem.heuristicInfo` to avoid redundant BFS calls. Admissible because Pacman must travel at least as far as the farthest food. Consistent by the triangle inequality — one step changes maze distance to any food by at most 1. Expanded only 4137 nodes on trickySearch, earning the optional extra credit (threshold: ≤7000).

## Question 6: Corners Problem Heuristic

Implemented `cornersHeuristic` using a greedy nearest-neighbor approach over unvisited corners with Manhattan distance. From the current position, repeatedly pick the closest unvisited corner and accumulate the Manhattan distances. Admissible because Manhattan distance never overestimates the actual maze path. Consistent by the triangle inequality — one step changes the heuristic by at most 1. Expands 692 nodes on mediumCorners (threshold for full credit is 1200).

## Question 5: Finding All the Corners

Implemented `CornersProblem` in `searchAgents.py`. The state is `(position, visited_corners)` where `visited_corners` is a tuple of 4 booleans indicating which corners have been reached. `getStartState` marks any corner matching the start position as already visited. `isGoalState` returns `True` when all four booleans are `True`. `getSuccessors` moves to valid adjacent positions and updates the visited tuple if the new position is a corner. Solves tinyCorners in 28 steps.

## Question 4: A* Search

Implemented `aStarSearch` in `search.py` using `util.PriorityQueue`. Same structure as UCS but the priority is `g(n) + h(n)` — cumulative cost plus the heuristic estimate to the goal. With `nullHeuristic` it reduces to UCS; with `manhattanHeuristic` it expands fewer nodes (221 vs 269 on mediumMaze).

## Question 3: Uniform Cost Search

Implemented `uniformCostSearch` in `search.py` using `util.PriorityQueue`. Each fringe entry stores `(state, actions, cost)` with the cumulative path cost as the priority. This guarantees the least-cost path is found first, unlike BFS which only minimizes the number of actions.

## Question 2: Breadth First Search

Implemented `breadthFirstSearch` in `search.py` using `util.Queue` for FIFO ordering. The structure is identical to DFS except the fringe is a Queue, which processes nodes level-by-level and guarantees the shortest path in terms of number of actions. Produces a 68-step optimal solution on mediumMaze.
