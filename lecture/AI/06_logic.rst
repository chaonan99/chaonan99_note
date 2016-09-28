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
:nowrap:
\begin{eqnarray}
P \rightarrow Q&\equiv \neg P \vee Q &\text{(implication)}\\
P \vee (Q \wedge R) &\equiv (P \vee R) \wedge (Q \vee R) &\text{(distributivity)}\\
P \wedge (Q \vee R) &\equiv (P \wedge Q) \vee (P \wedge R) &\text{} \\
\neg(P \vee Q) &\equiv \neg P \wedge \neg Q &\text{(DeMorgan's law)}\\
\neg (P \wedge Q) &\equiv \neg P \vee \neg Q &\text{} \\
P ∨ (P ∧ Q) &≡ P &\text{(absorption)} \\
P ∧ (P ∨ Q) &≡ P &\text{}
\end{eqnarray}

Defination of Predicate Logic
-----
* `Reference <http://www.cs.utexas.edu/~eberlein/cs301k/predLogic.pdf>`_
* A **predicate** is a **property** that a variable or a finite collection of variables can have.
* A predicate becomes a **proposition** when specific values are assigned to the variables.
* :math:`P(x_1, x_2, ..., x_n)` is called a predicate of n variables or n arguments.
* Domain and truth set

Quantifier
^^^^^
* **Universal quantifier** :math:`\forall`, **existential quantifier** :math:`\exists`
* Quantifier truns a predicate into a proposition
* The **scope** if a quantifier is the part of a statement in which variables are bound by the quantifier.
	* Eg: :math:`R ∨ \exists(P(x) ∨ Q(x))`, scope of :math:`\exists`: :math:` P(x) ∨ Q(x)`
* Distribution equation

.. math::
	\forall x(P(x)\vee Q(x))\equiv\forall xP(x)\vee \forall xQ(x)\\
	\exists x(P(x)\vee Q(x))\equiv\exists xP(x)\vee \exists xQ(x)\\
	\forall x(P(x)\vee Q(x))\rightarrow\forall xP(x)\vee \forall xQ(x) \\
	\exists x(P(x)\wedge Q(x))\rightarrow \exists xP(x)\wedge \exists xQ(x)
