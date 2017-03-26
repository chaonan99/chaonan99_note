# Automated and Cooperative Vehicle Merging at Highway On-Ramps
* [paper](http://ieeexplore.ieee.org/document/7534837/)
* Author: [Jackeline Rios-Torres](https://www.ornl.gov/staff-profile/jackeline-rios-torres), [Andreas A. Malikopoulos](http://www.andreas-malikopoulos.com/)

## Some New Concepts
* [Model predictive control](https://en.wikipedia.org/wiki/Model_predictive_control)
* Ramp metering: regulate the flow of vehicles merging into freeways to decrease traffic congestion
* Deceleration fuel cutoff (DFCO): terminates fuel injection at braking and the engine does not consume any fuel

## Contribution
* Hard constraint of collision aviodance and optimize fuel consumption
* Centralized, online closed-form

## Framework
* Merging zone $S$, control zone $L$.
* FIFO queue $i=N(t)+1$
* Model framework
    * Initial state and state equation: $$\dot{x}_i = f(t, x_i, u_i), \quad x_i(t_i^0)=x_i^0$$
    * State space and control input: $$u_i(t) = \dot{v_i},\quad x_i(t) = [p_i(t), v_i(t)]^\mathrm{T}$$
* Optimization
    * Fuel consumption model: $$\dot{f}_v = \dot{f}_{\mathrm{cruise}} + \dot{f}_{\mathrm{accel}}$$
    * where: $$\begin{aligned}\dot{f}_{\mathrm{cruise}}&=q_0 + q_1v(t)+q_2v^2(t)+q_3v^3(t)\\\dot{f}_{\mathrm{accel}}&=u(t)\cdot(r_0 + r_1v(t) + r_2v^2(t))\end{aligned}$$
    * Parameters are calculated from experimental data
    * The model does not yield fuel consumption for braking, i.e., when \(u(t)\) takes negative values
    * Figure:
        * ![image](https://farm3.staticflickr.com/2862/33598858525_09f30459d0_m_d.jpg)
    * Parameters are given. See original paper.
    * Constraints
        * \(u_{\min}\leq u_i(t) \leq u_{\max}, 0\leq v_{\min}\leq v_i(t)\leq v_{\max}\)
        * Safe distance \(\delta\)
        * Only one vehicle can be crossing the merging zone at a time
        * **Assumption**: The vehicle speed inside merging zone is constant
    * Optimize: **control input** + **gap between vehicles**

## Analysis
* Hard constraint for collision aviodance, based on some assumptions
* Hamiltonian Analysis ([Hamiltonian mechanics](https://en.wikipedia.org/wiki/Hamiltonian_mechanics#Mathematical_formalism))
* After some deductions (do not understand)
    + Optimal control strategy: \(u_i^* (t) = a_it + b_i\)

## Experiments
* 4 cars, same initial speed
    + Controller can avoid collision (merging zone occupy)
* 30 cars, same initial speed, no limitation on speed
    + Some car need to decelerate under road capacity constraint
* 30 cars, 13.4m/s for main road and 11.2m/s for secondary road
    + Car on main road has more chance to accelerate
* Compare with baseline: car on secondary road should stop and wait until main road is clean.
    + Fuel consumption lower
* High speed with speed limitation
    + Hard to find feasible solution