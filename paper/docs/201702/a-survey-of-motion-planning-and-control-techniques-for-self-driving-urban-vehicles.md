# A Survey of Motion Planning and Control Techniques for Self-driving Urban Vehicles

## People
* [Emilio Frazzoli](https://ares.lids.mit.edu/)

## Basic Concept on ITS and Self-Driving Cars
* Vehicle mobility model
* Typical constraints
    - Structure of the environment
    - Computational requirements
* On-board computation and wireless communication technology
* Collision free space
* Probabilistic planning formalisms

## History of Self-Driving Cars
* Self-driving cars have had a long history
    -  The idea has been around as early as in the 1920s, but it was not until the 1980s that driverless cars seemed like a real possibility
        + *E. D. Dickmanns and V. Graefe, “Dynamic monocular machine vision,” Machine vision and applications, vol. 1, pp. 223–240, 1988.*
        + A notable demonstration in 1994 resulting from the work was a 1,600 km drive by the VaMP driverless car, of which 95% was driven autonomously
* DARPA Grand Challenge in 2004
* DARPA Urban Challenge in 2007
* Recently more challenges
* Connected intelligent vehicles
* **SAE J3016 standard** 0 to 5 grading from fully human operated to fully autonomous.
    - **Level 0** a vehicle where all driving tasks are the responsibility of a human driver.
    - **Level 1** basic driving assistance such as adaptive cruise control, anti-lock braking systems and electronic stability control.
    -  **Level 2** advanced assistances uch as hazard-minimizing longitudinal/lateral control or emergency braking, often based upon set-based formal control theoretic methods to compute ‘worst-case’ sets of provably collision free (safe) states.
    - **Level 3** the system monitors the environment and can drive with full autonomy under certain conditions, but the human operator is still required to take control if the driving task leaves the autonomous system’s operational envelope.
    - **Level 4** automation is capable of fully autonomous driving in certain conditions and will safely control the vehicle if the operator fails to take control upon request to intervene.
    - **Level 5**  fully autonomous in all driving modes.

## Decision-Making Hierarchy Used In Driveless Cars
### Overview
* Driverless cars -- essentially autonomous decision-making systems
* Process a stream of observations from on-board sensors
    - Radars
    - LIDARs
    - Cameras
    - GPS/INS units
    - Odometry
* Additional information
    - Prior knowledge about the road network
    - Rules of the road
    - Vehicle dynamics
    - Sensor models
* Intelligent vehicle research aims at automating as much of the driving task as possible
    - partition and organize perception and decision-making tasks into a hierarchical structure

### Components of the hierarchical structure
* Figure II.1 in this paper
    - ![decision making hierarchy](http://img.blog.csdn.net/20170225104014143?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

* Route Planning
    - Road network as a directed graph (with weighted edges)
    - Dijkstra or A^* impractical
    - Challenge: return an optimal route on a continent-scale network in milliseconds
    - Already a family of algorithms have been found to achieve that after a one-time pre-processing
        + *H. Bast, D. Delling, A. Goldberg, M. Müller-Hannemann, T. Pajor, P. Sanders, D. Wagner, and R. F. Werneck, “Route planning in transportation networks,” arXiv preprint arXiv:1504.05140, 2015.*
* Behavioral Decision Making
    - Interact with other traffic participants, take  driving conventions and rules of the road into account
    - Select driving behavior based on the following
        + Perceived behavior of other traffic participants (what if in group decision making? Directly fetched?)
        + Road conditions
        + Signals from infrastructure
    - Both driving contexts and the behaviors available in each context can be modeled as finite sets
        + Model each behavior as a state in a finite state machine (adopted by most teams for DARPA challenges)
    - The problem of **intention prediction** and estimation of future trajectories of other vehicles, bikes and pedestrians has also been studied
        + Gaussian mixture models
        + Gaussian process regression (Google self-driving system for intention prediction)
    -  Probabilistic planning formalisms
        + Markov Decision Processes (MDPs) and their generalizations
* Motion Planning
    - Examples of the output of behavioral layer (input of motion planning)
        + cruise-in-lane
        + change-lane
        + turn-right/left
    - Translate the selected behavior into a path or trajectory that can be tracked by the low-level feedback controller
    - Requirement of motion planning
        + Dynamically feasible for the vehicle
        + Comfortable for the passenger
        + Avoid collisions with obstacles detected by the on-board sensors
    - Exact solution to the motion planning problem are mostly computationally intractable: numerical approximation methods
        + Variational methods
        + Graph-search
        + Incremental tree-based approaches
* Vehicle control
    - Feedback controller

### Models of mobility of car-like vehicles
* Begin: vehicle configuration (pose and position in the world)
    - Determain the coordinate system for the configuration space (e.g. the planar coordinate of a point on the car together with the car’s heading)
    - Planar rigid-body motions (represented by the Special Euclidean group in two dimensions, SE(2))

#### The Kinematic Single-Track Model
* ![kinematic single-track model](http://img.blog.csdn.net/20170225112044453?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvY2huMTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
* Assumptions (nonholonomic constraint)
    - No slip between the wheels and the ground. Wheels can rotate freely.
    - Front wheel has an added degree of freedom.
    - (The two assumptions makes the car unable to  lateral displacement without simultaneously moving forward)
* Math formulation
    - $\delta$ is a small angle
    - The motion of the points $p_r$ and $p_f$ must be collinear with the wheel operation (no-slip assumption)
    - Rear wheel: $$\dot{p_r}\cdot\hat{e_y}\cos(\theta)-(\dot{p_r}\cdot\hat{e_x})\sin(\theta) = 0$$
    - Front wheel: $$\dot{p_f}\cdot\hat{e_y}\cos(\theta+\delta)-(\dot{p_f}\cdot\hat{e_x})\sin(\theta+\delta) = 0$$
* Another form:
    - $\dot{x_r} = v_r\cos \theta$
    - $\dot{y_r} = v_r\sin \theta$
    - $\dot{\theta} = \frac{v_r}{l}\tan{\delta}$
    - 
