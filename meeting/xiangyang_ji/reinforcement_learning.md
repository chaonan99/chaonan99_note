# Reinforcement Learning
* 3rd, November, Thursday

## Approaches to Reinforcement Learning
* Value-based
* Policy-based
* Model-based

## Deep Reinforcement Learning
* Use deep network to describe value function/policy/model
* Optimize loss function by stochastic gradient descent
* Not stable

## DQN
* Q-learning: `Q^*(s,a)=E_{a'}[r+\gamma\max_{a'}Q(s',a')|s,a]`
* Problem of Q-learning with deep network
	* Data is sequential: successive samples are correlated, non-iid
	* Policy changes rapidly with slight changes to Q-values
		* Policy may oscillate
* How DQN solve these problems
* Development
	* Double DQN
	* Prioritized replay
	* Duelling network
	* Asynchronous reinforcement learning (A3C)

## Drawbacks
* DAta inefficient
* Long time to train
* Safe
* Low level abstraction
* Transfer poorly
* Hard to explain

## Prograssive research area
* Prograssive NN
* Attention
* Generative model
