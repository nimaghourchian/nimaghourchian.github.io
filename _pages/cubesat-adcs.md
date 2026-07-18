---
layout: single
title: "Attitude Determination and Control System"
permalink: /projects/cubesat-adcs/
author_profile: false
---


<style>
.page__content {
  padding-top: 1.5rem;
}
</style>

This competition gave participating teams the freedom to define their own CubeSat missions and design the spacecraft around the resulting requirements. After evaluating several mission concepts, our team developed Cubisa, a 3U CubeSat intended to demonstrate technologies relevant to tether-based space-debris removal.
The spacecraft consisted of a the main satellite, named Q, and a detachable module, named Bisa, representing a target object. The proposed mission involved stabilizing the spacecraft after orbital injection, deploying Bisa using an inter-satellite tether, observing its relative motion through onboard imaging, retrieving and reconnecting it, reorienting the combined spacecraft, and finally deploying a drag sail to accelerate orbital decay.
Our design progressed through conceptual design and detailed design which ultimately placed us among the top four out of 52 teams nationwide who received funding to develop an engineering prototype. 

<img src="/images/cubesat-team.jpg" alt="3U CubeSat ADCS team" style="width: 100%; max-width: 850px; border-radius: 10px; margin-bottom: 1.5rem; margin-top: 1.5rem;">


My role as a member of the Attitude Determination and Control System team involved translating the mission profile into ADCS requirements, researching and selecting the control architecture, developing the orbital and attitude-dynamics simulation, defining reference frames and coordinate transformations, implementing and tuning the attitude controller, designing orbital day/night sensor-selection logic, combining sensor measurements to reduce noise and drift, and validating the system through software-in-the-loop and processor-in-the-loop testing.

This project gave me experience with the complete development process of a spacecraft control subsystem—from interpreting mission requirements and studying candidate algorithms to mathematical modelling, sensor management, controller tuning, simulation, and embedded integration.
More importantly, it taught me that developing a control system is not merely a matter of implementing equations from a paper. Every theoretical decision must remain consistent with the spacecraft’s mission, coordinate conventions, sensor availability, actuator constraints, computational hardware, and validation strategy.




