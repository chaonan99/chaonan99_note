# Graph search strategy
14th, Sept.

## Problem solving
### State space
+ From initial state to objective through medium states
+ Eg: Sentence parsing
	* Input string (initial state)
	* Substitute according to **regulations**
	* Output if the string is a sentence (objective)
+ Eg: Judge if a snippet is in C language
+ Eg: [Traveling salesman problem (TSP)](https://en.wikipedia.org/wiki/Travelling_salesman_problem)
	* Can be formalized with string
+ Eg: Missionary and wild man

### Basic graph search algorithm
+ [Breadth first search (BFS)](https://en.wikipedia.org/wiki/Breadth-first_search)
![2016_09_14_e6e5114f2ea8255bddfa6a037d4a4fd](http://oa5omjl18.bkt.clouddn.com/2016_09_14_e6e5114f2ea8255bddfa6a037d4a4fd.png "BFS for shortest path")
+ [Depth first search (DFS)](https://en.wikipedia.org/wiki/Depth-first_search)
![2016_09_14_39c8ece6634d7f5e527217be12886139](http://oa5omjl18.bkt.clouddn.com/2016_09_14_39c8ece6634d7f5e527217be12886139.png "DFS shortest path")
+ [Uniform cost search (Dijkstra's algorithm)](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)

![Dijkstra](https://upload.wikimedia.org/wikipedia/commons/5/57/Dijkstra_Animation.gif "Dijkstra's algorithm")
+ Hill-climbing method
	* [Manhattan distance](https://en.wiktionary.org/wiki/Manhattan_distance) or [L^1 norm](http://mathworld.wolfram.com/L1-Norm.html)
	* Search for the node who has **the smallest L^1 norm** (greedy algorithm) to the target.

### Heuristic search
> Project 1!!!
* Heuristic function ![equation](http://latex.codecogs.com/svg.latex?h%28n%29), which takes a node *n* and returns a non-negative real number that is an estimate of the path cost from node *n* to a goal node. [ref](http://artint.info/html/ArtInt_56.html)
* ![equation](http://latex.codecogs.com/svg.latex?A%5E%2A) algorithm
![2016_09_14_c6f7fe4c9b349749bce3263214821e39](http://oa5omjl18.bkt.clouddn.com/2016_09_14_c6f7fe4c9b349749bce3263214821e39.png "A^* algorithm")

### Property of algorithm
* Completeness
* Admissibility