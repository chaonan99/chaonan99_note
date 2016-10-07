# Graph search strategy
14th, Sept.

## State space
+ From initial state to objective through medium states
+ Assumptions:
	* The agent has perfect knowledge of the state space (full observability)
	* The agent has a set of actions that have known deterministic effects
	* Some states are goal staes, which the agent wants to reach
	* A **solution** is a sequence of actions that will get the agent from its current state to a goal state
+ Eg: Sentence parsing
	* Input string (initial state)
	* Substitute according to **regulations**
	* Output if the string is a sentence (objective)
+ Eg: Judge if a snippet is in C language
+ Eg: [Traveling salesman problem (TSP)](https://en.wikipedia.org/wiki/Travelling_salesman_problem)
	* Can be formalized with string
+ Eg: Missionary and wild man

## Tricolor Algorithms
* [Reference](http://www.cs.cornell.edu/courses/cs2112/2012sp/lectures/lec24/lec24-12sp.html)
* And abstract description of graph traversal
* Graph nodes are assigned one of three colors that can change over time
	* **White** undiscovered
	* **Black** reachable and done
	* **Gray** discovered but not done

## Basic Graph Search Algorithm
### [Breadth first search (BFS)](https://en.wikipedia.org/wiki/Breadth-first_search)
* Illustration
![2016_09_14_e6e5114f2ea8255bddfa6a037d4a4fd](http://oa5omjl18.bkt.clouddn.com/2016_09_14_e6e5114f2ea8255bddfa6a037d4a4fd.png "BFS for shortest path")

* Pseudocode
```
// let s be the source node
frontier = new Queue()
mark root visited (set root.distance = 0)
frontier.push(root)
while frontier not empty {
    Vertex v = frontier.pop()
    for each successor v' of v {
	if v' unvisited {
	    frontier.push(v')
	    mark v' visited (v'.distance = v.distance + 1)
	}
    }
}
```

* [Application](http://www.geeksforgeeks.org/applications-of-breadth-first-traversal/)

### [Depth first search (DFS)](https://en.wikipedia.org/wiki/Depth-first_search)
* Illustration
![2016_09_14_39c8ece6634d7f5e527217be12886139](http://oa5omjl18.bkt.clouddn.com/2016_09_14_39c8ece6634d7f5e527217be12886139.png "DFS shortest path")

* Pseudocode
```
DFS(Vertex v) {
    mark v visited
    set color of v to gray
    for each successor v' of v {
	if v' not yet visited {
	    DFS(v')
	}
    }
    set color of v to black
}
```

* [Application](http://www.geeksforgeeks.org/applications-of-depth-first-search/)

### [Uniform cost search (Dijkstra's algorithm)](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)

![Dijkstra](https://upload.wikimedia.org/wikipedia/commons/5/57/Dijkstra_Animation.gif "Dijkstra's algorithm")

### [Hill-climbing method](https://en.wikibooks.org/wiki/Artificial_Intelligence/Search/Iterative_Improvement/Hill_Climbing)
* [Manhattan distance](https://en.wiktionary.org/wiki/Manhattan_distance) or [L^1 norm](http://mathworld.wolfram.com/L1-Norm.html)
* Search for the node who has **the smallest L^1 norm** (greedy algorithm) to the target.
* Can be applied to any problem where the current state allows for an accurate evaluation function.
* [Application](http://www.psychicorigami.com/2007/05/12/tackling-the-travelling-salesman-problem-hill-climbing/) on [TSP](https://en.wikipedia.org/wiki/Travelling_salesman_problem).

## Heuristic Search
* For every node, define a cost function:
	![equation](http://latex.codecogs.com/svg.latex?f%28n%29%20%3D%20g%28n%29%2Bh%28n%29)
* [Heuristic function](http://artint.info/html/ArtInt_56.html)
![equation](http://latex.codecogs.com/svg.latex?h%28n%29), which takes a node *n* and returns a non-negative real number that is an estimate of the path cost from node *n* to a goal node.
* Basic search algorithm can be attributed to heuristic search:
	+ BFS: ![equation](http://latex.codecogs.com/svg.latex?h%28n%29%20%3D%200%2C%20g%28n%29%20%3D%20d%28n%29)
	+ DFS: ![equation](http://latex.codecogs.com/svg.latex?h%28n%29%20%3D%20%5Cinf%2C%20g%28n%29%20%3D%200%2C%20f%28n%29%20%3D%20h%28n%29)

### [![equation](http://latex.codecogs.com/svg.latex?A%5E%2A) algorithm](http://artint.info/html/ArtInt_57.html)
![2016_09_14_c6f7fe4c9b349749bce3263214821e39](http://oa5omjl18.bkt.clouddn.com/2016_09_14_c6f7fe4c9b349749bce3263214821e39.png "A^* algorithm")

* A* is implemented by treating the frontier as a priority queue ordered by ![equation](http://latex.codecogs.com/svg.latex?f%28p%29).
* **Proposition** (Admissibility of A*) A* always finds an optimal path, if one exists, and the first path found to a goal is optimal, if
	+ the branching factor is finite (each node has only a finite number of neighbors),
	+ arc costs are greater than some ![equation](http://latex.codecogs.com/svg.latex?%5Cepsilon%20%3E%200), and
	+ ![equation](http://latex.codecogs.com/svg.latex?h%28n%29) is a lower bound on the actual minimum cost of the lowest-cost path from n to a goal node.

## Influencial Factors of Speed of A*
* Extended node number
* Computation cost of h(x)
