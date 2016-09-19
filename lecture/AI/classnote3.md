# Graph search strategy
19th, Sept.

## Introduction of computation complexity
* Reference: computers and intractability

### Compare pros and cons of different algorithm
* Experiment? Need to run in the same environment
* Complexity analysis. Independent from environment
* **Scale** examples:
	* binary tree search (depth = n): ![equation](http://latex.codecogs.com/svg.latex?2%5En)
	* Traveling Salesman Problem (TSP, n cities): ![equation](http://latex.codecogs.com/svg.latex?n%21)
* Reference: [UCI lecture](https://www.ics.uci.edu/~eppstein/161/960312.html)

### Classification of problems
* P: Problems that can be solved in polynomial time
* NP: This stands for "nondeterministic polynomial time" where nondeterministic is just a fancy way of talking about **guessing** a solution
	* Does not stand for "non-polynomial"!!!
	* A problem is in NP if you can quickly (in polynomial time) test whether a solution is correct (without worrying about how hard it might be to find the solution)
	* ![equation](http://latex.codecogs.com/svg.latex?P%20%5Csubseteq%20NP)
* Polynomial simplify-able
	* PA: sort scores of the whole class; PB: find the highest score in the class
	* PA is polynomial simplify-able with PB (PA can be solved by calling PB and do other constant operations)
	* ![equation](http://latex.codecogs.com/svg.latex?P_A%20%5Cpropto%20P_B)
	* **PB is at least the same hard with PA**
* NP-completeness: judgment problem ![equation](http://latex.codecogs.com/svg.latex?P_1%20%5Cin%20NP), for all other judgment problem ![equation](http://latex.codecogs.com/svg.latex?P%27%20%5Cin%20NP), we have ![equation](http://latex.codecogs.com/svg.latex?P%27%20%5Cpropto%20P_1), then ![equation](http://latex.codecogs.com/svg.latex?P_1) is NP-completeness
	* NP completeness is the most hard problem of all NP problems
* NP-complete class
* NP hard

