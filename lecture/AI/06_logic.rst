Predicate Logic
=====
Sept. 28th, 2016

Reference on this topic origin from `UTexas CS301k Logic <http://www.cs.utexas.edu/~eberlein/cs301k/cs301ktopics.html>`_.

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
* :math:`\neg` denotes **not**
* :math:`\vee` denotes **or**
* :math:`\wedge` denotes **and**
* :math:`\rightarrow` For propositions :math:`P` and :math:`Q`, the **implication** or **conditional statement** :math:`P\rightarrow Q` is false when :math:`P` is true and :math:`Q` is false, and is true otherwise. :math:`P` is called the premise or hypothesis, and :math:`Q` is called the conclusion.

* :math:`\leftrightarrow` The **biconditional** of statements :math:`P` and :math:`Q`, denoted :math:`P \leftrightarrow Q`, is read ":math:`P` if and only if :math:`Q`" (or ":math:`P` is necessary and sufficient for :math:`Q`"), and is true if :math:`P` and :math:`Q` have the same truth values, and false otherwise.

Logic equivalent and identities
^^^^^
* **Logically equivalent**: :math:`R\equiv S`.
* Important identities:
.. math::
	P \rightarrow Q&\equiv \neg P \vee Q &\text{(implication)}\\
	P \vee (Q \wedge R) &\equiv (P \vee Q) \wedge (P \vee R) &\text{(distributivity)}\\
	P \wedge (Q \vee R) &\equiv (P \wedge Q) \vee (P \wedge R) &\text{} \\
	\neg(P \vee Q) &\equiv \neg P \wedge \neg Q &\text{(DeMorgan's law)}\\
	\neg (P \wedge Q) &\equiv \neg P \vee \neg Q &\text{} \\
	P \vee (P \wedge Q) &\equiv P &\text{(absorption)} \\
	P \wedge (P \vee Q) &\equiv P &\text{}

Normal form
^^^^^
* `Disjuctive normal form (DNF) <https://en.wikipedia.org/wiki/Disjunctive_normal_form>`_: OR of ANDs
* `Conjuctive normal form (DNF) <https://en.wikipedia.org/wiki/Disjunctive_normal_form>`_: AND of ORs
* `Conversion <http://math.stackexchange.com/questions/214338/how-to-convert-to-conjunctive-normal-form>`_ of disjuctive and conjuctive normal form.

Defination of Predicate Logic
-----
* `Reference (link failure) <http://www.cs.utexas.edu/~eberlein/cs301k/predLogic.pdf>`_
* `First-order logic <http://mathworld.wolfram.com/First-OrderLogic.html>`_
* A **predicate** is a **property** that a variable or a finite collection of variables can have.
* A predicate becomes a **proposition** when specific values are assigned to the variables.
* :math:`P(x_1, x_2, ..., x_n)` is called a predicate of n variables or n arguments.
* Domain and truth set

Quantifier
^^^^^
* **Universal quantifier** :math:`\forall`, **existential quantifier** :math:`\exists`
* Quantifier truns a predicate into a proposition.
* The **scope**: if a quantifier is the part of a statement in which variables are bound by the quantifier.
	* Eg: :math:`R \vee \exists(P(x) \vee Q(x))`, scope of :math:`\exists` is :math:`P(x) \vee Q(x)`
* Distribution equation

.. image:: http://oa5omjl18.bkt.clouddn.com/2016_09_28_a024d27e17fccf08ad134615e5e9d1.png

Prenex Normal Form
-----
* `Reference <http://www.csd.uwo.ca/~lila/prenex.pdf>`_
* Defination: A formula is in **prenex normal form** if it is of the form
.. math::
	Q_1x_1 Q_2x_2 \dots Q_nx_nB
where :math:`Q_i(i = 1, \dots, n)` is :math:`\forall` or :math:`\exists` and the formula :math:`B` is quantifier free.

* Any expression can be converted into prenex normal form. (How to!!!!)
	#. Eliminate all occurrences of → and ↔ from the formula in question
		* :math:`A \rightarrow B \equiv \neg A \vee B`
		* :math:`A \leftrightarrow B \equiv (A \wedge B) \vee (\neg A \wedge \neg B)`
	#. Move all negations inward such that, in the end, negations only appear as part of `literals <https://en.wikipedia.org/wiki/Literal_(mathematical_logic)>`_
		* De Morgan’s Laws
	#. Standardize the variables apart (when necessary)
		.. image:: http://oa5omjl18.bkt.clouddn.com/2016_09_28_89ad976190c6f562aeef42f32522712.png
	#. The prenex normal form can now be obtained by moving all quantifiers to the front of the formula
		.. image:: http://oa5omjl18.bkt.clouddn.com/2016_09_28_d543964ddf96a1b4e5f3b46c4d8f1.png
* Example:
	.. image:: http://oa5omjl18.bkt.clouddn.com/2016_09_29_209dfc97bf5097cfb62d28b76de7bf.png

Resolution Principle
-----
* `Reference <http://logic.stanford.edu/intrologic/notes/chapter_05.html>`_
* First occurred in 1965, published by Alan Robinson.
* Refutation-complete: if you write any set of sentences in first order logic which are unsatisfiable (i.e., taken together they are false, in that they have no models), then the resolution method will eventually derive the False symbol, indicating that the sentences somehow contradict each other.

Clausal form
^^^^^
* A `literal <https://en.wikipedia.org/wiki/Literal_(mathematical_logic)>`_ is either an atomic sentence or a negation of an atomic sentence.
* A clausal sentence is either a literal or a `disjunction <https://en.wikipedia.org/wiki/Logical_disjunction>`_(connected by OR operation) of literals.
* A `clause <https://en.wikipedia.org/wiki/Clause_(logic)>`_ is the set of literals in a clausal sentence.
	* Empty set {} is also a clause. It is `equivalent to <https://en.wikipedia.org/wiki/Logical_equivalence>`_ an empty disjunction and is `unsatisfiable <https://en.wikipedia.org/wiki/Satisfiability>`_ (cannot be true).
* An arbitrary set of Propositional Logic sentences can be deducted to an equivalent set of clauses.

Rule of inference (Resolution principle)
^^^^^
* Intuition
	* :math:`{p, q}`:  p is true or q is true.
	* :math:`{\neg q, r}`: q is false or r is true.
	* q is either true or false: either p is true or r is true.
	* :math:`{p, r}`
* Principle:
.. image:: http://oa5omjl18.bkt.clouddn.com/2016_10_01_e43d2c58ecc5298c21341b250bffa9f.png

* Resolution is not generatively complete, i.e. it is not possible to find resolution derivations for all clauses that are logically entailed by a set of premise clauses.
* (`Herbrand's Theorem <https://en.wikipedia.org/wiki/Herbrand%27s_theorem>`_) If a set :math:`\Delta` of clauses is unsatisfiable, then there is guaranteed to be a resolution derivation of the empty clause from :math:`\Delta`.