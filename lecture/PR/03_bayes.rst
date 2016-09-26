Bayes Decision Theory (2)
=====

Loss Function
-----
* State space :math:`\Omega` has :math:`c` classes, :math:`\Omega = {\omega_1,\dots,\omega_c}`
* We have :math:`a` possible actions :math:`{\alpha_1,\dots,\alpha_a}`
* The loss function :math:`\lambda(\alpha_i|\omega_j)` is the loss incurred for taking action :math:`\alpha_i` when the class is :math:`\omega_j`.
* *Zero-one loss function*

.. image:: http://oa5omjl18.bkt.clouddn.com/2016_09_26_395257ca65dc711c4ca5cef31ada51c.png

Expected loss
^^^^^
* The *expected loss* or conditional risk is by definition

.. math::
	R(\alpha_i|\mathbf{x}) = \sum_{j=1}^c\lambda(\alpha_i|\omega_j)P(\omega_j|\mathbf{x})
	:label: eq:exloss

* *Zero-one conditional risk*

.. math::
	R(\alpha_i|\mathbf{x}) = \sum_{j\not=i}P(\omega_j|\mathbf{x}) = 1 - P(\omega_i|\mathbf{x})
	:label: eq:zoexloss

Overall risk
^^^^^
* Define *a decision rule* :math:`\alpha(x)`, a mapping from the input feature
space to an action :math:`\mathbf{R}\mapsto{\alpha_1,\dots,\alpha_a}`

