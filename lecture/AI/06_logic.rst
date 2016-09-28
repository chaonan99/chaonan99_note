Predicate Logic
=====
Sept. 28th, 2016

`Propositional Logic <https://en.wikipedia.org/wiki/Propositional_calculus>`_
-----
* `Reference <http://www.cs.utexas.edu/~eberlein/cs301k/propLogic.pdf>`_
* Zeroth-order logic
* True or false
* Example::

	Premise 1: If it's raining then it's cloudy.
	Premise 2: It's raining.
	Conclusion: It's cloudy.

Logic operations (connectives)
^^^^^
* :math:`\neg` denotes not
* :math:`\vee` denotes or
* :math:`\wedge` denotes and

Defination of Predicate Logic
-----
* `Reference <http://www.cs.utexas.edu/~eberlein/cs301k/predLogic.pdf>`_
* A **predicate** is a **property** that a variable or a finite collection of variables can have.
* A predicate becomes a **proposition** when specific values are assigned to the variables.
* :math:`P(x_1, x_2, ..., x_n)` is called a predicate of n variables or n arguments.
* Domain and truth set

Quantifier
^^^^^
* Universal quantifier :math:`\forall`, existential quantifier :math:`\exists`
* Quantifier truns a predicate into a proposition
* Distribution equation
.. math::
	\forall x(P(x)\vee Q(x))\equiv\forall xP(x)\vee \forall xQ(x)\\
	\exists x(P(x)\wedge Q(x))\rightarrow \exists xP(x)\wedge \exists xQ(x)\\
	\exists x(P(x)\vee Q(x))\equiv\exists xP(x)\vee \exists xQ(x)\\
	\forall x(P(x)\vee Q(x))\rightarrow\forall xP(x)\vee \forall xQ(x)