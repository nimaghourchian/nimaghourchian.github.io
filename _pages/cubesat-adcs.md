---
layout: single
title: "3U CubeSat Attitude Determination and Control System"
permalink: /projects/cubesat-adcs/
author_profile: false
---


This competition gave participating teams the freedom to define their own CubeSat missions and design the spacecraft around the resulting requirements. After evaluating several mission concepts, our team developed Cubisa, a 3U CubeSat intended to demonstrate technologies relevant to tether-based space-debris removal.
The spacecraft consisted of a the main satellite, named Q, and a detachable module, named Bisa, representing a target object. The proposed mission involved stabilizing the spacecraft after orbital injection, deploying Bisa using an inter-satellite tether, observing its relative motion through onboard imaging, retrieving and reconnecting it, reorienting the combined spacecraft, and finally deploying a drag sail to accelerate orbital decay.
Our design progressed through conceptual design, detailed design, and prototype development, ultimately placing among the top four teams out of 52 participants nationwide.

<img src="/images/cubesat-team.jpg" alt="3U CubeSat ADCS team" style="width: 100%; max-width: 850px; border-radius: 10px; margin-bottom: 1.5rem; margin-top: 1.5rem;">


## My Role
I was one of two team members responsible for the Attitude Determination and Control System, which had to determine the spacecraft’s orientation and generate the control commands required throughout the different mission phases.
My work focused on:
- translating the mission profile into ADCS requirements;
- researching and selecting the control architecture;
- developing the orbital and attitude dynamics simulation;
- defining the reference frames and coordinate transformations;
- implementing and tuning the attitude controller;
- designing orbital day/night sensor-selection logic;
- combining sensor measurements to reduce noise and drift;
- and validating the ADCS through software-in-the-loop simulation.

## Mission-Driven ADCS Design
The mission created several distinct attitude control requirements. Following deployment into orbit, the spacecraft first had to reduce its initial angular velocity and establish a stable orientation. It then had to maintain the pointing conditions required for communication, imaging, tether deployment, retrieval of the Bisa module, and the final drag-sail deployment maneuver.
The proposed mission profile included detumbling and subsystem checkout, tether deployment and separation, relative observation and retrieval of Bisa, a 90-degree spacecraft reorientation, and deployment of the drag sail. The ADCS therefore had to support several operating modes rather than a single fixed-pointing condition.
## Controller Selection
Choosing the control strategy was one of the most difficult early design decisions. The competition did not prescribe a controller, and the mission requirements could not be translated directly into a ready-made solution.
My teammate and I reviewed numerous research papers and compared candidate spacecraft attitude-control approaches before converging on a quaternion-feedback PD controller for attitude stabilization and reference tracking.
Quaternions provided a compact attitude representation without the singularities associated with Euler-angle descriptions. However, using them consistently required careful treatment of quaternion conventions, attitude error, multiplication order, reference frames, and sign ambiguity. A controller can be mathematically elegant and still launch the simulation directly into the graveyard if one frame transformation is reversed.
For initial detumbling, the control architecture used a B-dot controller, which generated magnetic control commands based on changes in the measured geomagnetic field. After the angular rate had been sufficiently reduced, the system transitioned to quaternion-feedback control for nominal attitude regulation.
## Orbital and Attitude-Dynamics Model
An important part of this work was establishing consistent coordinate systems throughout the model. The orbital model, spacecraft body, reference attitude, sensor measurements, geomagnetic field, and commanded control moments all had to be expressed in compatible frames.
Even a small inconsistency between the body and orbital frames could cause the controller to produce a mathematically valid command in precisely the wrong direction—which is a very sophisticated way of losing a satellite.
## Attitude Determination and Sensor Management
The ADCS architecture used measurements from a three-axis gyroscope, magnetometer, and sun/horizon sensor.
Each sensor had different advantages and limitations:
- The gyroscope provided angular-rate measurements but was affected by noise and accumulated drift.
- The magnetometer measured the geomagnetic-field vector in the spacecraft body frame.
- The sun sensor provided an external attitude reference during illuminated portions of the orbit but became unavailable during eclipse.

<img src="/images/adcs_architecture.png" alt="3U CubeSat ADCS team" style="width: 100%; max-width: 850px; border-radius: 10px; margin-bottom: 1.5rem;">

Because the available measurements changed as the spacecraft moved between orbital daylight and darkness, we implemented switching logic to select the appropriate sensor configuration during each condition. The sensor measurements were then combined to reduce noise and compensate for the limitations of relying on any individual sensor.
The conceptual design also incorporated camera-based horizon detection and observation of the Bisa module. Image processing tasks were assigned to a Raspberry Pi, while attitude control execution was handled by the STM32-based onboard computer.
## Controller Tuning
The quaternion-feedback controller required extensive tuning.
The gains had to provide acceptable convergence without introducing excessive oscillation or control effort. 
Tuning was performed iteratively in Simulink while observing the spacecraft attitude, quaternion error, angular velocity, and commanded control moments. The process showed that controller tuning could not be separated from actuator limitations, sensor noise, or the spacecraft inertia model.
## Software-in-the-Loop Validation
The ADCS was validated through software-in-the-loop testing in Simulink.
The Simulink model allowed us to evaluate the behaviour of the complete control loop before deploying it to the target processor. 
The SIL stage was particularly valuable for identifying issues involving quaternion conventions, coordinate transformations, controller gains, switching logic, and actuator saturation
Embedded ADCS Architecture
The final onboard-computer architecture used an STM32H563 microcontroller for real time OBC and ADCS operations and a Raspberry Pi Zero 2W for camera processing and higher-level communication tasks.
The embedded ADCS executed at 10 Hz and followed a modular processing sequence:
Sensor acquisition → Data preparation → ADCS algorithm → Magnetic-moment calculation → Magnetorquer command
Gyroscope, magnetometer, and horizon/sun-sensor data were collected and supplied to the control model. The controller calculated three-axis magnetic-moment commands, which were transmitted to the magnetorquer drivers. The Simulink control model was subsequently incorporated into a processor-in-the-loop implementation on the STM32 platform.
## Outcome
This project gave me experience with the complete development process of a spacecraft control subsystem—from interpreting mission requirements and studying candidate algorithms to mathematical modelling, sensor management, controller tuning, simulation, and embedded integration.
More importantly, it taught me that developing a control system is not merely a matter of implementing equations from a paper. Every theoretical decision must remain consistent with the spacecraft’s mission, coordinate conventions, sensor availability, actuator constraints, computational hardware, and validation strategy.
