# Search Assignment Answers

## Question 1: Depth First Search

Implemented DFS in search.py using util.Stack for LIFO ordering. Each fringe entry stores state and action allowing path to be reconstructed. A visited set prevents re-expanding already seen states (graph search). Successors are pushed in the order returned by getSuccessors, which makes a 130 step solution on mediumMaze.

## Question 2: Breadth First Search

Implemented BFS in search.py using util.Queue for FIFO ordering. Its is similar to DFS except the fringe is a queue. This processes nodes level-by-level and gets the shortest path in terms of # actions. Creates a 68 step optimal solution on mediumMaze.

## Question 3: Uniform Cost Search

Implemented uniformCostSearch in search.py using util.PriorityQueue. Each fringe entry stores state, actions, and cost. The cumulative path cost is the priority. This is to find the least cost path first which unlike BFS that only minimizes the number of actions.

## Question 4: A* Search

Implemented aStarSearch in search.py using util.PriorityQueue. Similar structure as UCS but the priority is g(n) + h(n) — cumulative cost + heuristic estimate to the goal. With nullHeuristic it reduces to UCS, with manhattanHeuristic it expands fewer nodes (221 vs 269 on mediumMaze).

## Question 5: Finding All the Corners

Implemented CornersProblem in searchAgents.py. The states are position and visited_corners, visited_corners is a tuple of 4 booleans that shows which corners have been reached. getStartState marks any corner matching the start position as visited. isGoalState returns True when all four booleans are True. getSuccessors moves to valid adjacent positions and updates the visited tuple if the new position is a corner. Solves tinyCorners in 28 steps.

## Question 6: Corners Problem Heuristic

Implemented cornersHeuristic with greedy nearest neighbor approach over unvisited corners with Manhattan distance. From the current position you pick the closest unvisited corner and accumulate the Manhattan distances. this works because Manhattan distance never overestimates the actual maze path. From the triangle inequality one step changes the heuristic by at most 1. Expands 692 nodes on mediumCorners.

## Question 7: Eating All the Dots Heuristic

Implemented foodHeuristic using the maze distance to farthest remaining food pellet with results cached in problem.heuristicInfo so that you can avoid redundant BFS calls. Works because Pacman must travel, bare minimum, as far as the farthest food. Consistent by the triangle inequality one step changes maze distance to any food by at most 1. Expanded only 4137 nodes on trickySearch.

## Question 8: Suboptimal Search

Implemented AnyFoodSearchProblem.isGoalState to return True when the current position contains food (self.food[x][y]). Implemented findPathToClosestDot by solving that problem with search.bfs finding the shortest path to the nearest food. This is suboptimal overall because greedily going to the nearest dot can force backtracking across the maze. A small detour now might avoid a long one later which can be seen visually.
