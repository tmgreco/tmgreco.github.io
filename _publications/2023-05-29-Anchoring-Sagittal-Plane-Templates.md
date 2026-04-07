---
title: "Anchoring sagittal plane templates in a spatial quadruped"
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

Controller Design
======

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
Further analytical work (link to Hopf paper) aims to provide a more general stability proof that will

<!-- slidesurl: 'https://academicpages.github.io/files/slides1.pdf' -->
