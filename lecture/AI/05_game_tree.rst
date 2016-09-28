Game Tree
=====

`Reference\: Game playing basics <http://www.uni-weimar.de/medien/webis/teaching/lecturenotes/search/unit-en-game-playing-basics.pdf>`_

Basic concept
-----
* The game tree search here focuses on *two-player, perfect-information* games.
	* Two-players, take turns to play.
	* Any player know history moves (no possibility).
* A game tree is a representation of all possible plays of a game.
	* The root node represents the initial state :math:`s`.
	* Leaf nodes represent goal states.
	* Each path from the root :math:`s` to a leaf nodes represents a complete game.

Game Tree
-----
* A game tree is a tree whose nodes (both inner nodes and leaf nodes) are either of type "Max" or "Min"
	1. All nodes at the same level of a game tree are of the same type.
	2. Max nodes and Min nodes alternate between any two consecutive levels (One layer all OR-nodes, one layer all AND-nodes).
* Graphic notation and summary:
	* □ = player 1 = Max  player = own view = Max node = OR node
	* O = player 2 = Min  player = adversarial view = Min node = AND node
* Players play optimum.
* Use `minimax algorithm <https://en.wikipedia.org/wiki/Minimax>`_ to search.

Example: `Tic-tac-toe <https://en.wikipedia.org/wiki/Tic-tac-toe>`_
-----
* Can define an evaluation function :math:`f` (assume player 1 => X):
	* For the current state, place all X in the spaces and count three X marks to be :math:`a`.
	* Place all O in the spaces and count three O marks to be :math:`b`.
	* Then :math:`f=a-b`
* For OR search, choose MAX :math:`f`. For AND search, choose MIN :math:`f`.

Game Playing Introduction
-----
* From any node :math:`s` in tree :math:`T`, decide a :math:`T^+` tree (subtree of :math:`T`) for player Max and :math:`T^-` tree for player Min.
	* Two strategies :math:`T^+`, :math:`T^-`, of Max and Min respectively, *share at each level either one or no edge!!!*.
	* The intersection of two strategies :math:`T^+`, :math:`T^-`, defines the leaf (:math:`T^+ \spcap T^−`), which corresponds to the final position of the game.
	* Important property

.. math::
	\min\limits_{T^-}  \max\limits_{T^+}status(T^+ \cap T^-) = status(s) =  \max\limits_{T^+} \min\limits_{T^-}status(T^+ \cap T^-)

.. image:: http://oa5omjl18.bkt.clouddn.com/2016_09_26_968785f92ea2cd53bc79db54621f03.png
	:alt: :math:`T^+` and :math:`T^-` tree

`Alpha–beta pruning <https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning>`_
-----
`See this video \(15 minutes\) <https://www.youtube.com/watch?v=xBXHtz4Gbdo>`_

.. image:: https://upload.wikimedia.org/wikipedia/commons/9/91/AB_pruning.svg
	:scale: 50 %
	:alt: Source\: Wikipedia

`Monte Carlo Tree Search <https://en.wikipedia.org/wiki/Monte_Carlo_tree_search>`_
-----
