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
<details class="project-details">
  <summary>Absolute Visual Localization</summary>

  <div class="details-content">
    <p>
      A pretrained ResNet-50 network was used to extract visual features from each UAV image and each satellite-map tile.
The final convolutional features were aggregated using Generalized Mean Pooling, or GeM pooling, to generate a compact global descriptor for each image. The descriptors were normalized and stored in a searchable database.
This allowed the system to compare the general appearance of the UAV image with large numbers of satellite tiles without performing expensive pixel-level matching against every candidate.
Hierarchical Map Retrieval
The basemap was divided into large parent tiles and smaller subtiles.
During localization, the UAV image descriptor was first searched against the parent-tile database. The most similar parent tiles were selected as possible geographic regions.
The second retrieval stage then searched only the subtiles belonging to those parent regions. This reduced the candidate area and prevented the fine-matching stage from having to process the complete basemap.
Both retrieval stages used FAISS, a library designed for efficient similarity search in high-dimensional feature spaces.
Fine Feature Matching
Global image descriptors are useful for identifying visually similar regions, but they do not prove that two images show exactly the same location.
The top candidate subtiles were therefore passed to a finer matching stage based on a LiteSAM/LoFTR-style feature matcher.
This stage produced corresponding feature points between the UAV image and each candidate satellite tile. Candidate tiles were then ranked using the number and confidence of the detected correspondences.
This made it possible to reject tiles that looked generally similar but did not contain geometrically consistent local features.
Homography and Geographic Position
After the best satellite tile had been selected, the matched feature points were used to estimate a projective transformation between the UAV image and the map tile.
A homography was calculated using RANSAC, which helped reject incorrect or inconsistent correspondences.
The centre of the UAV image was then projected into the satellite tile using the estimated homography. Because the selected satellite tile was georeferenced, the corresponding pixel could be converted into map coordinates and then into WGS84 latitude and longitude.
The output of the absolute-localization branch was therefore a globally referenced position estimate together with an inlier ratio that could be used as an indicator of match quality.

    </p>
  </div>
</details>

<details class="project-details">
  <summary>Relative Visual Localization</summary>

  <div class="details-content">
    <p>
      The Relative Visual Localization branch estimated short-term UAV motion by comparing consecutive camera frames.
Unlike absolute localization, it did not search the satellite basemap. Instead, it examined how visual features moved from one UAV image to the next.
Feature Detection and Matching
SIFT was used to detect keypoints and calculate descriptors in consecutive frames.
The descriptors were matched using a FLANN-based matcher, and Lowe’s ratio test was applied to remove ambiguous matches.
If a sufficient number of valid feature correspondences remained, a partial affine transformation was estimated between the two frames.
From this transformation, the system extracted:
•	horizontal pixel displacement;
•	vertical pixel displacement;
•	change in yaw.
Converting Image Motion into Ground Motion
The measured pixel displacement had to be converted into a physical displacement.
The conversion used:
•	the UAV altitude;
•	the camera field of view;
•	the image width and height.
These values were used to approximate the ground-sampling distance of each image. Pixel motion could then be converted into metres.
The displacement was rotated into a north–east reference frame using the accumulated yaw estimate. Successive motion estimates were integrated to produce a continuous local trajectory.
This method was fast enough to process image sequences at a nominal rate of 10 Hz, but because each estimate depended on the previous one, errors accumulated over time.

    </p>
  </div>
</details>

<details class="project-details">
  <summary>Kalman filtering</summary>
  <div class="details-content">
    <p>
      After generating the visual-position estimates, I implemented a linear Kalman filter to combine them with inertial and barometric measurements and produce a smoother, continuous navigation state.
During the prediction stage, acceleration measurements from the simulated IMU were used as control inputs. Because the accelerometer measurements were initially expressed in the UAV body frame, the current roll, pitch, and yaw were used to transform them into the NED frame. Gravity was then removed before the acceleration was passed to the filter. The kinematic model propagated both position and velocity using the measured acceleration.
When a recent visual-navigation measurement was available, it was used to correct the predicted position. Barometric pressure was independently converted into altitude and used to constrain the vertical position. During development, simulated GPS was retained as an initialization and fallback measurement when no sufficiently recent visual estimate was available; it was not intended to be the primary source during GPS-denied operation.
The filter output contained the estimated three-dimensional position and velocity. The local NED position was then converted back into latitude, longitude, and altitude using the initial geographic reference. This fused geographic estimate was stored in shared memory and transmitted to ArduPilot through MAVLink as an external GPS input.
The Kalman filter reduced short-term measurement noise and provided a continuous state estimate between visual-position updates. However, it did not completely solve the main real-time problem. The absolute visual-localization measurements could arrive after the UAV had already moved, while the filter treated accepted measurements as observations of the current state. Consequently, delayed visual updates could create inconsistencies in the estimated position and contribute to instability when the output was used as a direct GPS replacement in the ArduPilot control loop.

    </p>
  </div>
</details> 

The two localization branches served different purposes.
Absolute Visual Localization estimated a globally referenced latitude and longitude by finding the satellite-image region corresponding to the current UAV image.
Relative Visual Localization estimated how the UAV moved between successive camera frames. It produced frequent motion updates but accumulated drift because small errors were integrated over time.
The Kalman filtering stage combined the two. Relative localization maintained a continuous trajectory, while occasional absolute-localization results were used to correct the accumulated drift.
The resulting output was converted into geographic coordinates and transmitted to ArduPilot through MAVLink as an external navigation measurement intended to replace simulated GPS.


<video autoplay muted loop playsinline controls style="width: 100%; max-width: 900px; border-radius: 10px; margin-bottom: 1.5rem;">
  <source src="/videos/gps-denied-navigation.mp4" type="video/mp4">
</video>



