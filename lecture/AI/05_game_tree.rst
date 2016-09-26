Game Tree
=====

`Reference <http://www.uni-weimar.de/medien/webis/teaching/lecturenotes/search/unit-en-game-playing-basics.pdf>`_

Basic concept
-----
* The game tree search here focuses on *two-player, perfect-information* games.
	* Two-players, take turns to play.
	* Any player know history moves (no possibility).
* A game tree is a representation of all possible plays of a game.
	* The root node represents the initial state :math:`s`.
	* Leaf nodes represent goal states.
	* Each path from the root :math:`s` to a leaf nodes represents a complete game.

Game Tree Search
-----
* A game tree is a tree whose nodes (both inner nodes and leaf nodes) are either of type "Max" or "Min"
	1. All nodes at the same level of a game tree are of the same type.
	2. Max nodes and Min nodes alternate between any two consecutive levels (One layer all OR-nodes, one layer all AND-nodes).
* Graphic notation and summary:
	* □ = player 1 = Max  player = own view = Max node = OR node
	* O = player 2 = Min  player = adversarial view = Min node = AND node

Example: `Tic-tac-toe <https://en.wikipedia.org/wiki/Tic-tac-toe>`_
-----
* Can define an evaluation function :math:`f` (assume player 1 => X):
	* For the current state, place all X in the spaces and count three X marks to be :math:`a`.
	* Place all O in the spaces and count three O marks to be :math:`b`.
	* Then :math:`f=a-b`
* For OR search, choose MAX :math:`f`. For AND search, choose MIN :math:`f`.

`Alpha–beta pruning <https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning>`_
-----
`See this <https://www.youtube.com/watch?v=xBXHtz4Gbdo>`_

.. image:: https://upload.wikimedia.org/wikipedia/commons/9/91/AB_pruning.svg
	:scale: 50 %
`Monte Carlo Tree Search <https://en.wikipedia.org/wiki/Monte_Carlo_tree_search>`_
-----
