# Introduction of computation complexity
19th, Sept.

* Reference: computers and intractability
* Reference: [UCI lecture](https://www.ics.uci.edu/~eppstein/161/960312.html)

## Compare pros and cons of different algorithm
* Experiment? Need to run in the same environment
* Complexity analysis. Independent from environment
* **Scale** examples:
	* binary tree search (depth = n): ![equation](http://latex.codecogs.com/svg.latex?2%5En)
	* Traveling Salesman Problem (TSP, n cities): ![equation](http://latex.codecogs.com/svg.latex?n%21)

## Classification of problems
![complexity](https://upload.wikimedia.org/wikipedia/commons/a/a0/P_np_np-complete_np-hard.svg)

![P,NP and NP complete](https://upload.wikimedia.org/wikipedia/commons/b/bc/Complexity_classes.svg)

* **P**: Problems that can be solved in polynomial time
* [**NP**](https://en.wikipedia.org/wiki/NP_%28complexity%29): This stands for "nondeterministic polynomial time" where nondeterministic is just a fancy way of talking about **guessing** a solution
	* Does not stand for "non-polynomial"!!!
	* A problem is in NP if you can quickly (in polynomial time) test whether a solution is correct (without worrying about how hard it might be to find the solution)
	* ![equation](http://latex.codecogs.com/svg.latex?P%20%5Csubseteq%20NP)
* [Reduction (polynomial reduction)](https://en.wikipedia.org/wiki/Reduction_%28complexity%29)
	* Eg: `PA`: sort scores of the whole class; `PB`: find the highest score in the class
	* `PA` is polynomial reducible to `PB` if an algorithm for solving `PB` efficiently (if it existed) could also be used as a subroutine to solve `PA` efficiently
	* ![equation](http://latex.codecogs.com/svg.latex?P_A%20%5Cpropto%20P_B)
	* **`PB` is at least as hard as `PA`**
* [**NP-completeness**](https://en.wikipedia.org/wiki/NP-completeness): judgment problem ![equation](http://latex.codecogs.com/svg.latex?P_1%20%5Cin%20NP), for all other decision problems ![equation](http://latex.codecogs.com/svg.latex?P%27%20%5Cin%20NP), we have ![equation](http://latex.codecogs.com/svg.latex?P%27%20%5Cpropto%20P_1), then ![equation](http://latex.codecogs.com/svg.latex?P_1) is NP-completeness
	* NP completeness is the most hard problem of all NP problems
	* Any given solution to an NP-complete problem can be verified in polynomial time
	* But there is no known efficient way to locate a solution in the first place
* What to do when facing NP-complete problem?
* NP-complete set
* **NP hard**

