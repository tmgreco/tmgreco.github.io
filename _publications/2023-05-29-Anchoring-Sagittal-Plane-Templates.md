---
title: "Anchoring Sagittal Plane Templates in a Spatial Quadruped"
collection: publications
category: conferences
permalink: /publication/2023-05-29-Anchoring-Sagittal-Plane-Templates
excerpt: 'This paper introduces a new controller that stabilizes the motion of a spatial quadruped around sagittal-plane templates. It enables highly dynamic gaits and transitional maneuvers formed from parallel and sequential compositions of such planar templates in settings that require significant out-of-plane reactivity. The controller admits formal guarantees of stability with some modest assumptions. Experimental results validate the reliable execution of those planar template-based maneuvers, even in the face of large lateral, yaw, and roll incurring disturbances. This spatial anchor, fixed in parallel composition with a variety of different parallel and sequential compositions of sagittal plane templates, illustrates the robust portability of provably interoperable modular control components across a variety of hardware platforms and behaviors.'
date: 2023-05-29
venue: '2023 IEEE International Conference on Robotics and Automation (ICRA)'
paperurl: 'https://ieeexplore.ieee.org/document/10161488'
citation: 'T. Greco and D. E. Koditschek, "Anchoring Sagittal Plane Templates in a Spatial Quadruped," 2023 IEEE International Conference on Robotics and Automation (ICRA), London, United Kingdom, 2023, pp. 12113-12119, doi: 10.1109/ICRA48891.2023.10161488.'
---
Background
======
Testing unordered list
- Introduce templates and anchors
- Historically, templates are often planar; anchoring must handle out-of-plane disturbances.
- Moving from planar robots (e.g. Minitaur) to "spatial" robots (e.g. Mini Cheetah, Spirit, Unitree, AnyMAL, Spot) requires more careful anchoring that uses out-of-plane degrees of freedom to actively stabilize templates.

Controller Design
======
Let $$R$$ be the orientation of the robot in $$SO(3)$$ represented by the rotation matrix that maps from the body frame to the world frame.  Focusing on the case in which the robot has two laterally-paired legs in contact with the ground (e.g. either both hind legs or both front legs), we introduce a controller that aims to align the robot's hips with its toes.  Assuming that the $$y$$-axis of the body frame corresponds to the vector pointing from the right hip to the left hip (within the leg pair) and establishing our world frame so that the world-frame $$y$$-axis points from the right toe to the left toe, the desired set of orientations can be defined as

<p align="center">$$ \mathcal{P} = \{ R \ |\ Ry = y\} $$</p>


where $$y = [0, 1, 0]^T$$ is a constant vector in $$\mathbb{R}^3$$.

Using $$\Phi = 1 - y^T R y$$ as a virtual potential function, we design a potential-dissipative controller to stabilize $$\mathcal{P} \subset SO(3)$$.  Note that $$\Phi(R) = 0$$ if and only if $$R \in \mathcal{P}$$.

Formal Results
======
Exploiting the structure of this potential-dissipative controller yields two formal stability results:
1. If no torque is exerted by the template dynamics, total energy on $$SO(3)$$ acts as a LaSalle function, and $$P$$ is an asymptotically stable equilibrium.
2. If the template stabilizes the pitch to a fixed point within the template manifold $$P$$, the anchoring makes that point in $$P$$ locally stable in $$SO(3)$$.
Details about these proofs can be found in the paper and the accompanying technical report (links coming soon).

Empirical Results
======

Steady State Gaits
------

Transitional Behaviors
------

Disturbance Rejection
-------

Future Work
======
Further analytical work (link to Hopf paper) will strengthen the analytical results by providing explicit basins of attraction and relaxing restrictions on template dynamics to encompass the templates used in these experiments.  Future empirical work will move towards 3D templates and

<!-- slidesurl: 'https://academicpages.github.io/files/slides1.pdf' -->
