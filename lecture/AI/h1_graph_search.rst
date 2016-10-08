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
5. Compare the performance w/ & w/o :math:`\alpha`-:math:`\beta` prune
	* Without :math:`\alpha`-:math:`\beta` prune: DFS algorithm will search the whole tree.
	* With :math:`\alpha`-:math:`\beta` prune: first search subtree in the left and the maximizer gets value -2. When searching subtree in the right, the minimizer will get -2 for the second succeeding leaf node. As -2 is not larger than -2, the right subtree will be pruned and the last leaf node won’t be visited.
6. Proof the optimality of :math:`A^*` algorithm.
	#. Assuming that there exists a node :math:`n` that is expanded under algorithm :math:`A_2`, we will prove that this node will be expanded by algorithm :math:`A_1`.
	#. According to admisibility of :math:`A^*`, :math:`h(n)` is an underestimation of the actual cost :math:`h^*(n)`, and note that the cost of the goal state is given by
	.. math:: f(G) = g(n)+h^*(n)
	where :math:`G` is the goal. Thus, given :math:`h_1(n)<h_2(n)<h^*(n)`, we can get
	.. math:: h_1(n)+g(n)<h_2(n)+g(n)<h^*(n)+g(n)
	That is to say
	.. math:: f_1(n)<f_2(n)<f(G)

	#. :math:`A*` is implemented by treating the frontier as a priority queue ordered by :math:`f(n) = g(n) + h(n)`, so before getting the goal state :math:`G`, node :math:`n` will be given priority access. This is true for all the node in the close list of :math:`A_2`. So the nodes expanded by :math:`A_1` will be no less than :math:`A_2`.
7. Eight-puzzle
	#. Using BFS and DFS to find a path from initial state to goal state
		* BFS (eliminate repetition)
			.. image:: http://oa5omjl18.bkt.clouddn.com/2016_10_07_bfs.gv.png
		* DFS (best case)
			.. image:: http://oa5omjl18.bkt.clouddn.com/2016_10_07_dfs.png
	#. Compare BFS and DFS
		In this problem, BFS can always be sure to find a path with minimal moves, but the complexity increases exponentially with the depth of search tree. DFS can't be sure to find the optimal solution. In this problem, we should limit the depth of the search tree to avoid cycle. So DFS can't always find a solution in a limited time for eight-puzzle problem. But sometimes it will happen to find a solution at a lower cost as is shown in the graph above.
	#. :math:`A^*` search
		:math:`g(n)`: depth of the search tree.
		:math:`h(n)`: Sum of Manhattan Distance for every block from its current position to the goal position.


