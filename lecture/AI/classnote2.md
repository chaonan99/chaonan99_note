# Graph search strategy
14th, Sept.

## Problem solving
* State space
	+ From initial state to objective through medium states
	+ Eg: Sentence parsing
		* Input string (initial state)
		* Substitute according to **regulations**
		* Output if the string is a sentence (objective)
	+ Eg: Judge if a snippet is in C language
	+ Eg: [Traveling salesman problem (TSP)](https://en.wikipedia.org/wiki/Travelling_salesman_problem)
		* Can be formalized with string
	+ Eg: Missionary and wild man
* Search in state space
	+ [Breadth first search (BFS)](https://en.wikipedia.org/wiki/Breadth-first_search)
	![BFS](https://upload.wikimedia.org/wikipedia/commons/3/33/Breadth-first-tree.svg "BFS")
	![2016_09_14_e6e5114f2ea8255bddfa6a037d4a4fd](http://oa5omjl18.bkt.clouddn.com/2016_09_14_e6e5114f2ea8255bddfa6a037d4a4fd.png "BFS for shortest path")
	+ [Depth first search (DFS)](https://en.wikipedia.org/wiki/Depth-first_search)
	![DFS](https://upload.wikimedia.org/wikipedia/commons/1/1f/Depth-first-tree.svg "DFS")
