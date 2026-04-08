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
Abstract
======
This paper introduces a new controller that stabilizes the motion of a spatial quadruped around sagittal-plane templates.  It enables highly dynamic gaits and transitional maneuvers formed from parallel and sequential compositions of such planar templates in settings that require significant out-of-plane reactivity. The controller admits formal guarantees of stability with some modest assumptions. Experimental results validate the reliable execution of those planar template-based maneuvers, even in the face of large lateral, yaw, and roll incurring disturbances.  This spatial anchor, fixed in parallel composition with a variety of different parallel and sequential compositions of sagittal plane templates, illustrates the robust portability of provably interoperable modular control components across a variety of hardware platforms and behaviors.

<!-- ![Disturbance Recovery while Bounding](/images/perturbation_bound_dramatic.gif) -->
<figure style="text-align: center;">
  <img src="/images/perturbation_bound_dramatic.gif" alt="Disturbance Recovery while Bounding" style="display: block; margin: 0 auto; width: 640px;">
  <figcaption style="margin-top: 12px;"> Spirit's spatial anchoring controller recovers from a strong rolling disturbance. The resulting perturbation is incurred while engaged in the energetic sagittal plane pitching required by the bounding gait.  Despite the high adversarial velocity in roll, the anchoring controller enables the robot to regain its balance and resume stable bounding.</figcaption>

</figure>

Background
======
Separating the dynamics of a complex motion into a low-dimensional template (which describes the bulk motion) and a high-dimensional anchoring (which makes the low-dimensional template manifold attracting and invariant within the configuration space) has proved to be an effective method of describing animal locomotion and generating behaviors for robots.  Controllers constructed by the composition of planar templates have yielded agile and robust sagittal-plane behaviors, including steady-state gaits [De and Koditschek, 2018] and leaping behaviors that enable complex interactions with objects in the environment [Pedipulation, Door-Opening].  However, their implementation on quadrupeds has largely been restricted to lower-DOF robots (e.g. Minitaur) whose dynamics closely match these planar models.  Executing these behaviors on quadrupeds with 12 actuated degrees of freedom requires the use of out-of-plane DOFs to stabilize the template submanifold without disturbing the dynamics within that manifold.  To this end, we introduce a novel anchoring controller to make the sagittal plane an attracting and invariant submanifold within $$SE(3)$$.

Controller Design
======
Let $$R$$ be the orientation of the robot in $$SO(3)$$ represented by the rotation matrix that maps from the body frame to the world frame.  Focusing on the case in which the robot has two laterally-paired legs in contact with the ground (e.g. either both hind legs or both front legs), we introduce a controller that aims to align the robot's hips with its toes.  Assuming that the $$y$$-axis of the body frame corresponds to the vector pointing from the right hip to the left hip (within the leg pair) and establishing our world frame so that the world-frame $$y$$-axis points from the right toe to the left toe, the desired set of orientations can be defined as

<p align="center">$$ \mathcal{P} = \{ R \ |\ Ry = y\} $$</p>


where $$y = [0, 1, 0]^T$$ is a constant vector in $$\mathbb{R}^3$$.

Using $$\Phi = 1 - y^T R y$$ as a virtual potential function, we design a potential-dissipative controller to stabilize $$\mathcal{P} \subset SO(3)$$.  Note that $$\Phi(R) = 0$$ if and only if $$R \in \mathcal{P}$$.  As detailed in the paper, $$\Phi$$ is a Morse-Bott function on $$SO(3)$$.

The potential-dissipative function takes the form
<p align="center"> $$\tau = -\nabla \Phi(R) - K_D \omega $$ </p>
where $$\nabla \Phi(R) = y \times Ry$$ is the gradient of $$\Phi$$ and $$K_D = \mathbf{diag}([k_1, 0, k_2])$$ is a positive semidefinite damping matrix.

While this controller stabilizes the orientation of the robot's body, a simple PD controller keeps the body centered over the toes.


Formal Results
======
Exploiting the structure of this potential-dissipative controller yields two formal stability results:
1. If no torque is exerted by the template dynamics, total energy on $$SO(3)$$ acts as a LaSalle function, and $$\mathcal{P}$$ is an asymptotically stable equilibrium.
2. If the template stabilizes the pitch to a fixed point within the template manifold $$P$$, the anchoring makes that point in $$P$$ locally stable in $$SO(3)$$.
Details about these proofs can be found in the paper and the accompanying technical report (links coming soon).

Empirical Results
======
<!-- We implemented this controller on a Ghost Spirit quadruped, using a hierarchical structure to emphasize the compositional nature of this framework. Each of the three layers is defined as a separate C++ object. At the highest layer,
behavior objects govern the sequential or parallel composition of template objects, passing them high-level inputs and handling transitions between them. The template objects make a sagittal-plane approximation of the robot’s dynamics and output appropriate planar forces. The anchoring object takes these forces and calculates forces for each toe to exert in 3D space so that the robot’s dynamics in the sagittal plane match the template dynamics and the out-of-plane dynamics are governed by the controller.  The resulting behaviors described below all use the exact same implementation of the anchoring controller, using the same set of gains to scale $$\nabla\Phi$$ and $$K_D$$ without any behavior-specific retuning.  Furthermore, the template and behavior layers are the same controllers used in previous work with Minitaur, although it was not possible to directly reuse the code. -->

Steady State Gaits
------
The anchoring controller enabled Spirit to replicate the feedback-stabilized pronk and preflexively-stable bound originally developed for Minitaur (link to Minitaur paper coming soon).  For both gaits, the orientation controller keeps roll and yaw close to zero while preserving the underlying behavior of the coupled slot-hopper templates: when only mechanical coupling is present, the front and rear hop out of phase with each other (bounding), although adding feedback between the front and rear can force them to hop in phase with each other (pronking).

<!-- Trying to use a table for this -->
<table>
  <tr>
    <td align="center">
      <img src="/images/bound.gif" alt="GIF 1" width="480"><br>
      Bounding
    </td>
    <td align="center">
      <img src="/images/pronk.gif" alt="GIF 2" width="480"><br>
      Pronking
    </td>
  </tr>
</table>

Transitional Behaviors
------
The anchoring controller also demonstrated the ability to stabilize the mount, dismount, and box-jump originally developed for Minitaur (link to Minitaur paper coming soon).  Spirit successfully performed each behavior repeatedly five times out of five attempts, meeting the same measure of repeatability exhibited by Minitaur.  Despite these behaviors’ short stance phases and high-velocity flight phases, the anchoring reliably stabilized the out-of-plane motion of the robot.

<figure style="text-align: center;">
  <img src="/images/boxjump.gif" alt="Spirit Performing Boxjump Maneuver" style="display: block; margin: 0 auto; width: 640px;">
  <figcaption style="margin-top: 12px;"> Spirit performs the box-jump maneuver from [transitional pedipulation paper].</figcaption>

</figure>

Disturbance Rejection
-------
We tested the disturbance rejection capabilities of the anchoring controller when composed with the bounding and pronking gaits by subjecting the robot to unexpected pulls.  It withstood these perturbations well, recovering from over 80% of disturbances while continuing to execute the gait.  The following videos (coming soon!) show some representative trials; more can be found in the supplemental video accompanying the paper (link coming soon, available on the Kodlab youtube channel).  More details about the disturbance rejection results, including statistics about the disturbances and their respective recovery rates, can be found in the paper.
<!-- that caused out-of-plane velocities up to twice the peak velocity observed during undisturbed execution of the gait.  Of all the failures recorded, only one resulted in the robot failing to keep its balance; most were destabilizations of the gait itself (e.g. failing to continue to stay in place, or failing to ) -->

Examining the anchoring's ability to reject disturbances during the transitional behaviors proved more difficult.  The short timescale of the behaviors made it impractical to perturb the robot's velocity during the behavior and expect it to have enough time to recover before coming to rest.  Instead, we started the behavior with some offset in the yaw position and measured the robot's ability to complete the behavior anyway.  (More details and videos coming soon).

Future Work
======
Further analytical work (link to Hopf paper) will strengthen the analytical results by providing explicit basins of attraction and relaxing restrictions on template dynamics to encompass the templates used in these experiments.  Future empirical work will move towards 3D template models to perform more diverse and agile locomotion tasks.

<!-- slidesurl: 'https://academicpages.github.io/files/slides1.pdf' -->
