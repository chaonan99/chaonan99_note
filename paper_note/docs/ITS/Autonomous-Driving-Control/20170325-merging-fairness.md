# Merging lanes — fairness through communication
* [paper](https://www.researchgate.net/publication/262922650)

## Fairness Evaluation
* Used to determine merge order.
* A car with longer wait time should be given preference.
* Wait time starts from free-flow arrival time
    + Free-flow arrival time: the time when the car would have arrived at the merge point if not hindered by other cars
    + Calculation: with maximum acceleration to reach and hold the maximum speed until arriving the merging point.

## Zipper Merge Fairness
* Unfairness is worse with higher income traffic flow and higher difference between two incoming flows.
* Unfairness grows without bounds even for slightly unbalanced inflows.

## Achieving fairness
* Fairness is ensured when all cars are participants (IV running the algorithm)
* With non-participants, expected unfairness is finite (proved).
* Question: under a realistic driver model, is the unfairness still finite?

## Simulation
* NS-3
    * Intelligent Driver Model (IDM) for car following
    * 802.11p communication standard
* Two scenario
    * Constant permeability, increasing traffic flow
    * Constant traffic flow, increasing permeability

