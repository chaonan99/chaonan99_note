# And-or Tree
20th, Sept.

* Reference: [problem reduction representation](http://www.uni-weimar.de/medien/webis/teaching/lecturenotes/search/unit-en-representation2.pdf)

## [And-or tree/graph](https://en.wikipedia.org/wiki/And%E2%80%93or_tree)
![And-or tree](https://upload.wikimedia.org/wikipedia/commons/8/8a/Andortree.png)

* Arcs indicates `and`, no arcs indicates `or`
* Leaf nodes can be goal nodes (nodes with solved or trivial rest problems) or dead nodes (can't solve)

## Solution graphs
 Let `G` be an acyclic AND-OR graph, and let `n` be a node in `G`. A finite subgraph `H` of `G` is called a solution graph for `n` in `G` iff the following conditions hold:
* `H` contains the node `n`.
* If `H` contains an inner OR node, then `H` contains exactly one link to a successor node in `G` and this successor node.
* If `H` contains an inner AND node, then `H` contains all links to its successor nodes in `G` and all these successor nodes.
* The leaf nodes in H are goal nodes in `G`.
* `H` is minimal: it contains no additional nodes and edges.

A constructional defination:
![2016_09_21_7f9f5e388a6b644190563697729baea6](http://oa5omjl18.bkt.clouddn.com/2016_09_21_7f9f5e388a6b644190563697729baea6.png "Add Description")

> This defination is not necessarily minimal!!!

Example of solution graph

![2016_09_21_a04b208a3653209ee3bf3ef25111b76](http://oa5omjl18.bkt.clouddn.com/2016_09_21_a04b208a3653209ee3bf3ef25111b76.png "Add Description")

## Solved-labeling algorithm
* Solved-labeling without labeling

```python
# Input: G. A finite, acyclic AND-OR graph.
#        n. A node in G.
#        successors(n). Returns the successors of node n.
#        goal(n). Predicate that is True if n is a goal node.
# Output: The symbol True if a solution exists, False otherwise.

def solved-labeling(G, n, successors, goal):
  if |successors(n)|==0:
    if goal(n):
      return True
    else:
      return False
  for n' in successors(n):
    if solved-labeling(G, n', successors, goal):
      if OR_node(n):
        return True # One success is enough
    else:
      if AND_node(n):
        return False # One fail is too much
  if OR_node(n):
    return False # OR_node n has no solvable successor.
  else:
    return True #  All successors of AND_node n are solvable.
```

* Solved-labeling with labeling
```python
# Input: G. A finite, acyclic AND-OR graph.
#        n. A node in G.
#        successors(n). Returns the successors of node n.
#        goal(n). Predicate that is True if n is a goal node.
# Output: The symbol True if a solution exists, False otherwise.

def solved-labeling(G, n, successors, goal):
  if solved(n):
    return True
  if |successors(n)|==0:
    if goal(n):
      solved(n) = True
      return True
    else:
      return False
  for n' in successors(n):
    if solved-labeling(G, n', successors, goal):
      if OR_node(n):
        solved(n) = True
        return True # One success is enough
    else:
      if AND_node(n):
        return False # One fail is too much
  if OR_node(n):
    return False # OR_node n has no solvable successor.
  else:
    solved(n) = True
    return True #  All successors of AND_node n are solvable.
```

## Solution graphs with cycles

![2016_09_21_824372ff7a3fa4bd8d9aa3144e6e4d27](http://oa5omjl18.bkt.clouddn.com/2016_09_21_824372ff7a3fa4bd8d9aa3144e6e4d27.png "Add Description")

> Solved-labeling algorithm above doesn't check cycles and may entail cyclic synthesized even if there exists an acyclic solution graph.

## Hypergraphs

## Game Tree
[Ref](http://www.uni-weimar.de/medien/webis/teaching/lecturenotes/search/unit-en-game-playing-basics.pdf)