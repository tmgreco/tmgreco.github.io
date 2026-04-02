---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* Ph.D in Electrical and Systems Engineering, University of Pennsylvania, 2026 (expected)
* M.S. in Robotics, University of Pennsylvania, 2025
* B.S. in Engineering, Swarthmore College, 2019

Research experience
======
* Fall 2019 - Present: Graduate Researcher at University of Pennsylvania, GRASP Laboratory.
  * Implemented several agile locomotion skills, defined by parallel and sequential compositions of sagittal-plane dynamical models, in C++ on a Ghost Robotics Spirit quadruped.
  * Developed and implemented a nonlinear controller to stabilize the robot’s orientation during these behaviors.
  * Formally proved that this controller is asymptotically stable for a broad class of sagittal-plane behaviors.
  * Developed and implemented a bounding gait for uneven terrain using 3D dynamical models, illustrating that these models capture important aspects of robust locomotion.
  * Developed and implemented compositions of 3D dynamical models for leaping behaviors, highlighting the utility of these models for describing and executing contact-rich maneuvers.
  * Developed custom interfaces for teleoperation and logging.
  * Supervisor: Professor Daniel E. Koditschek.

* Fall 2024: Visiting Instructor at Swarthmore College
  * Taught Mobile Robotics, an upper-level engineering elective.
  * Presented lectures covering kinematics, dynamics, perception, motion planning, and control.
  * Led a lab in which students used ROS and Python to perform locomotion tasks with differential-drive robots.
  * Mentored students individually to solidify their understanding of conceptual and technical content of the course.

* Summer 2018: Undergraduate Research Fellow at Johns Hopkins University.
  * Used OpenCV and ArUco tags to estimate the pose of a mobile robot in real time for feedback control.
  * Designed a LabVIEW application to automate experiments by synchronizing control and data acquisition.
  * Supervisor: Professor Chen Li.

* Summers 2015 - 2017: Student Intern at Draper Laboratory, Cambridge MA.
  * Developed utilities in MATLAB and LabVIEW for data collection and processing.
  * Built hardware interfaces for sensors.

Skills
======
* Programming Languages:
  * C++
  * Python
  * MATLAB
  * Mathematica
  * C
* Robotics Tools:
  * ROS/ROS2
  * Gazebo
  * Drake
  * IsaacGym
* Controls:
  * Legged Locomotion
  * Dynamical Systems Theory
  * Nonlinear Controls
  * Convex Optimization
  * Model-Predictive Control
  * Trajectory Optimization
  * Whole-Body Control
  * Reinforcement Learning

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

<!-- Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul> -->

Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

<!-- Service and leadership
======
* Volunteer Foster for the Penn Vet Working Dog Center
* Member of Tau Beta Pi and Phi Beta Kappa -->
