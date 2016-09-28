Bayes Decision Theory (2)
=====

Loss Function
-----
* State space :math:`\Omega` has :math:`c` classes, :math:`\Omega = \{\omega_1,\dots,\omega_c\}`
* We have :math:`a` possible actions :math:`\{\alpha_1,\dots,\alpha_a\}`
* The loss function :math:`\lambda(\alpha_i|\omega_j)` is the loss incurred for taking action :math:`\alpha_i` when the class is :math:`\omega_j`.
* *Zero-one loss function*

.. image:: http://oa5omjl18.bkt.clouddn.com/2016_09_26_395257ca65dc711c4ca5cef31ada51c.png
	:scale: 50%

Expected loss
^^^^^
* The *expected loss* or conditional risk is by definition

.. math::
	R(\alpha_i|\mathbf{x}) = \sum_{j=1}^c\lambda(\alpha_i|\omega_j)P(\omega_j|\mathbf{x})

* *Zero-one conditional risk*

.. math::
	R(\alpha_i|\mathbf{x}) = \sum_{j\not=i}P(\omega_j|\mathbf{x}) = 1 - P(\omega_i|\mathbf{x})

Overall risk
^^^^^
* Define *a decision rule* :math:`\alpha(x)`, a mapping from the input feature
space to an action :math:`\mathbb{R}^d\mapsto\{\alpha_1,\dots,\alpha_a\}`
* The *overall risk* is the expected loss associated with a given decision
rule.
.. math:: R=\ointR(\alpha(\mathbf{x}|\mathbf{x}))p(\mathbf{x})d\mathbf{x}
* Bayes decision rule gives us a method for minimizing the overall risk.
* The *Bayes Risk* is the best we can do.

Bayes discrimnant
^^^^^
* :math:`g_i(\mathbf{x})` is a *discriminant function* for the i-th class.
* This classifier will assign a class :math:`\omega_i` to the feature vector :math:`\mathbf{x}` if
.. math:: g_i(\mathbf{x}) > g_j(\mathbf{x}) \forall j \not= i
* The minimum conditional risk corresponds to the maximum discriminant.
.. math:: g_i(\mathbf{x}) = −R(\alpha_i|\mathbf{x})
* :math:`g_i(\mathbf{x})` can be replaced by :math:`f(g_i(\mathbf{x}))` where :math:`f(.)` is a monotonically increasing function.

Bayes decision under normal density
^^^^^
* Multivariate Gaussian in d dimensions
.. math:: p(\mathbf{x})=\frac{1}{(2\pi)^{d/2}|\mathbf{\Sigma}|^{1/2}}\exp[-\frac{1}{2}(\mathbf{x}-\mathbf{\mu})^T\mathbf{\Sigma}^{-1}(\mathbf{x}-\mathbf{\mu})]
* If we assume normal densities, i.e., if p(x|ωi) ∼ N(µi
, Σi), then the
general discriminant is of the form
