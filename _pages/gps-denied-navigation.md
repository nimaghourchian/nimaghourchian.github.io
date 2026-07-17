---
layout: single
title: "Vision-Based GPS-Denied Navigation"
permalink: /projects/gps-denied-navigation/
author_profile: false
---





This project explored whether a UAV could estimate its position using only imagery and a georeferenced satellite basemap when GPS measurements were unavailable.
The system was developed as my bachelor’s final project. I designed and implemented the full localization pipeline, integrated its components, evaluated the resulting trajectory, and attempted to use the estimated position as a replacement for GPS inside a closed-loop flight simulation.

<img src="/images/visual-positioning-architecture.png" alt="Vision-based GPS-denied navigation architecture" style="display:block; width:70%; max-width:950px; border-radius:10px; margin:1.5rem auto;">

The complete navigation scenario was created in a simulated environment rather than using a physical UAV.
AirSim was used for simulating the UAV, its motion, camera, and flight dynamics. Cesium for Unreal supplied the geospatial environment and allowed the vehicle to fly over realistic terrain.
The UAV camera produced a sequence of downward-looking images as the vehicle travelled through the environment. These images represented the input that would otherwise be produced by an onboard camera during a real flight.
A separate georeferenced basemap was created using satellite imagery from Google Maps. The basemap was divided into tiles and subtiles that could be searched efficiently during localization.
Ground-truth coordinates from the simulation were used only for evaluation and comparison. The intended navigation estimate itself came from the visual-localization algorithms.

The navigation pipeline was divided into three main parts:
1.	Absolute Visual Localization
2.	Relative Visual Localization
3.	Kalman filtering 
The two localization branches served different purposes.
Absolute Visual Localization estimated a globally referenced latitude and longitude by finding the satellite-image region corresponding to the current UAV image.
Relative Visual Localization estimated how the UAV moved between successive camera frames. It produced frequent motion updates but accumulated drift because small errors were integrated over time.
The Kalman filtering stage combined the two. Relative localization maintained a continuous trajectory, while occasional absolute-localization results were used to correct the accumulated drift.
The resulting output was converted into geographic coordinates and transmitted to ArduPilot through MAVLink as an external navigation measurement intended to replace simulated GPS.

<details class="project-details">
  <summary>Absolute Visual Localization</summary>

  <div class="details-content">
    <p>
      Detailed explanation goes here.
    </p>
  </div>
</details>

<details class="project-details">
  <summary>Relative Visual Localization</summary>

  <div class="details-content">
    <p>
      Detailed explanation goes here.
    </p>
  </div>
</details>

<details class="project-details">
  <summary>Kalman-Filter State Estimation</summary>

  <div class="details-content">
    <p>
      Detailed explanation goes here.
    </p>
  </div>
</details>


<video autoplay muted loop playsinline controls style="width: 100%; max-width: 900px; border-radius: 10px; margin-bottom: 1.5rem;">
  <source src="/videos/gps-denied-navigation.mp4" type="video/mp4">
</video>



