Artificial Intelligence Homework Assignment 1
=====
Class 32, Haonan Chen (陈昊楠), 2013011449

1. Rules: (1). S <- ( ) (2). A <- S (3). A <- A,A (4). S <- (A)
	.. image:: http://oa5omjl18.bkt.clouddn.com/2016_10_07_67f72fddc12234f665659d56bb935ba.png
2. Irreversible arc example
	In game Tic-tac-toe or Go, the search tree is irreversible.
3. Application of typical graph search algorithms
	* BFS (bread first search): in P2P (peer to peer) network, bread first search is used to find all neighbor nodes.
	* DFS (depth first search): play game with only one solution, such as maze, or find a loop in a graph.
	* UCS (uniform cost search): also called Dijkstra's algorithm, can be used to find the shortest path in a route graph
	* HC (hill climbing): hill climbing can be applied to any problem where the current state allows for an accurate evaluation function, such as the travelling salesman problem. Solution: http://www.psychicorigami.com/2007/05/12/tackling-the-travelling-salesman-problem-hill-climbing/
4. Use case of and-or graph
	* Most two-player game can be described with and-or graph. For example,
5. Compare the performance w/ & w/o :math:`\alpha-\beta` prune
	* Without :math:`\alpha-\beta` prune: DFS algorithm will search the whole tree.
	* With :math:`\alpha-\beta` prune: first search subtree in the left and the maximizer gets value -2. When searching subtree in the right, the minimizer will get -2 for the second succeeding leaf node. As -2 is not larger than -2, the right subtree will be pruned and the last leaf node won’t be visited.
6. Proof the optimality of :math:`A*` algorithm.
	:math:`A*` is implemented by treating the frontier as a priority queue ordered by f(p) = cost(p) + h(p), where p is the path found, cost(p) is the cost of path p and h(p) is the heuristic function estimating the path cost from the end of p to the goal.
	In :math:`A*` algorithm, the element with minimum f-value is chosen at each time step. As h(p) is an underestimation of the actual cost, if there exists an optimal solution with finite cost, the f-value of nodes on the any solution path will be less than or equal to the f-value of the solution path itself. Thus, the f-value of nodes on an optimal solution path will be less than or equal to any non-optimal path. That is to say, if there exists a node on the frontier that leads to an optimal solution (?????)

	Admisibility: :math:`h(n)<h'(n)` where :math:`h'(n)` is the actual cost from node :math:`n` to the optimal goal.
7. Eight-puzzle
	#. Using BFS and DFS to find a path from initial state to goal state
		* BFS (eliminate repetition)
			.. image:: http://oa5omjl18.bkt.clouddn.com/2016_10_07_bfs.gv.png
		* DFS (best case)
			.. image:: http://oa5omjl18.bkt.clouddn.com/2016_10_07_dfs.png
	#. Compare BFS and DFS
		In this problem, BFS can always be sure to find a path with minimal moves, but the complexity increases exponentially with the depth of search tree. DFS can't be sure to find the optimal solution. In this problem, we should limit the depth of the search tree to avoid cycle. So DFS can't always find a solution in a limited time for eight-puzzle problem. But sometimes it will happen to find a solution at a lower cost as is shown in the graph above.
	#. A* search
		g: depth of the search tree
		h: Manhattan Distance

