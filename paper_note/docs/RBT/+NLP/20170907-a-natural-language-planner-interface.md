# A Natural Language Planner Interface for Mobile Manipulators
* [paper](http://groups.csail.mit.edu/rrg/papers/Howard_ICRA14.pdf)
* Author: [Thomas M. Howard](http://www.ece.rochester.edu/people/faculty/howard_tom/), Stefanie Tellex, [Nicholas Roy](https://www.csail.mit.edu/user/902)

## Outline
* Task: plan trajectory given natural language instruction in a plain ground with serval colored objects.
    * The environment is semantically labeled.
* Proposed model: DCG, Distributed Correspondence Graph

## DCG
* A probabilistic graphical model composed of random variables that represent language $\lambda$, groundings $\gamma$ and corrrespondence between language and groundings $\phi$ and factor $f$.
* Each factor  $f_{i_j}$  in the DCG model is influenced by the current phrase  $\lambda_i$ , correspondence variable  $\phi_{i_j}$ , grounding  $\gamma_{i_j}$ , and child phrase groundings $\gamma_{c_{i_j}}$.
* The parameters in each log-linear model  υυ  are trained from a parallel corpus of labeled examples for annotations and behaviors in the context of a world model $\Upsilon$ (known).

$$\underset{\phi \, \in \, \varPhi }{\arg \, \max }\; \prod _{i} \prod _{j} f_{i_{j}} \left( \phi _{i_{j}}, \gamma _{i_{j}}, \gamma _{c_{i_{j}}}, \lambda _{i}, \varUpsilon , \upsilon \right) . $$