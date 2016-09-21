# Graph Search (2)
20th, Sept.

* Reference: [problem reduction representation](http://www.uni-weimar.de/medien/webis/teaching/lecturenotes/search/unit-en-representation2.pdf)

## [And-or tree/graph](https://en.wikipedia.org/wiki/And%E2%80%93or_tree)
![And-or tree](https://upload.wikimedia.org/wikipedia/commons/8/8a/Andortree.png)

* Arcs indicates `and`, no arcs indicates `or`
* Leaf nodes can be goal nodes (nodes with solved or trivial rest problems) or dead nodes (can't solve)

### Solution graph
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

### Solved-labeling

```python
# Input: G. A finite, acyclic AND-OR graph.
#        n. A node in G.
#        successors(n). Returns the successors of node n.
#        goal(n). Predicate that is True if n is a goal node.
# Output: The symbol True if a solution exists, False otherwise.

def solved-labeling(G, n, successors, goal):
  if |successors(n)|==0:
    if ?(n):
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
```