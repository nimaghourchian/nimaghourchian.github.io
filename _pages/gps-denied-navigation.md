---
layout: single
title: "Vision-Based GPS-Denied Navigation"
permalink: /projects/gps-denied-navigation/
author_profile: true
---

<video autoplay muted loop playsinline controls style="width: 100%; max-width: 900px; border-radius: 10px; margin-bottom: 1.5rem;">
  <source src="/videos/gps-denied-navigation.mp4" type="video/mp4">
</video>

## Project Overview

<img src="/images/visual-positioning-architecture.png" alt="Vision-based GPS-denied navigation architecture" style="width: 100%; max-width: 950px; border-radius: 10px; margin: 1.5rem 0;">

This project explored whether a UAV could estimate its position using only imagery and a georeferenced satellite basemap when GPS measurements were unavailable.
The system was developed as my bachelor’s final project and was completed independently. I designed and implemented the full localization pipeline, integrated its components, evaluated the resulting trajectory, and attempted to use the estimated position as a replacement for GPS inside a closed-loop flight simulation.
The UAV and its camera were simulated in Unreal Engine using Microsoft AirSim, while Cesium for Unreal provided a geospatially accurate environment. As the UAV flew through the simulated environment, a downward-facing camera generated aerial images. These images were then compared with satellite imagery obtained from Google Maps to estimate the UAV’s geographic position.
The final system combined two different sources of visual information:
-	absolute localization using matches between the UAV image and the satellite basemap;
-	relative localization using motion between consecutive UAV images.
The objective was to combine the global accuracy of absolute localization with the speed and continuity of relative localization, then provide the fused position estimate to ArduPilot SITL as an external navigation source.

## Motivation
Conventional UAV navigation relies heavily on satellite-based positioning systems such as GPS. Although GPS is accurate and widely available, it can become unreliable or completely unavailable in several operating conditions.
Examples include urban environments with severe signal obstruction, deliberate jamming or spoofing, indoor or underground operation, and missions in which the vehicle must navigate without depending on external radio signals.
Vision-based localization offers a possible alternative. A camera can capture information about the terrain below the UAV, and this information can be compared with previously available satellite or aerial imagery. If the corresponding location can be identified, the UAV can estimate its position without directly using GPS.
However, this is difficult in practice. UAV imagery and satellite imagery may differ in scale, resolution, viewpoint, lighting, texture, image quality, and orientation. A localization system must also operate quickly enough for its output to remain useful to the flight controller.
This project therefore addressed two related problems:
1.	determining the UAV’s position from visual information;
2.	delivering that position with sufficiently low delay for real-time navigation.
The first problem was solved with promising results. The second became the main limitation of the completed system.

## Simulation Environment
The complete navigation scenario was created in a simulated environment rather than using a physical UAV.
AirSim was responsible for simulating the UAV, its motion, camera, and flight dynamics. Cesium for Unreal supplied the geospatial environment and allowed the vehicle to fly over realistic terrain generated from geographic data.
The UAV camera produced a sequence of downward-looking images as the vehicle travelled through the environment. These images represented the input that would otherwise be produced by an onboard camera during a real flight.
A separate georeferenced basemap was created using satellite imagery from Google Maps. The basemap was divided into tiles and subtiles that could be searched efficiently during localization.
Ground-truth coordinates from the simulation were used only for evaluation and comparison. The intended navigation estimate itself came from the visual-localization algorithms.
Overall System Architecture
The navigation pipeline was divided into three main parts:
1.	Absolute Visual Localization
2.	Relative Visual Localization
3.	Asynchronous Fusion and Delay Handling

The two localization branches served different purposes.
Absolute Visual Localization estimated a globally referenced latitude and longitude by finding the satellite-image region corresponding to the current UAV image.
Relative Visual Localization estimated how the UAV moved between successive camera frames. It produced frequent motion updates but accumulated drift because small errors were integrated over time.
The fusion stage combined the two. Relative localization maintained a continuous trajectory, while occasional absolute-localization results were used to correct the accumulated drift.
The resulting geographic position was intended to replace the simulated GPS measurement supplied to ArduPilot.
## Absolute Visual Localization
The Absolute Visual Localization branch was responsible for estimating the UAV’s global position from a single aerial image.
Searching every satellite tile using detailed feature matching would have been computationally expensive. I therefore designed the system as a hierarchical retrieval and verification pipeline.
## Global Image Representation
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
## Relative Visual Localization
The Relative Visual Localization branch estimated short-term UAV motion by comparing consecutive camera frames.
Unlike absolute localization, it did not search the satellite basemap. Instead, it examined how visual features moved from one UAV image to the next.
Feature Detection and Matching
SIFT was used to detect keypoints and calculate descriptors in consecutive frames.
The descriptors were matched using a FLANN-based matcher, and Lowe’s ratio test was applied to remove ambiguous matches.
If a sufficient number of valid feature correspondences remained, a partial affine transformation was estimated between the two frames.
From this transformation, the system extracted:

-	horizontal pixel displacement;
-	vertical pixel displacement;
-	change in yaw.

Converting Image Motion into Ground Motion
The measured pixel displacement had to be converted into a physical displacement.
The conversion used:
-	the UAV altitude;
-	the camera field of view;
-	the image width and height.

These values were used to approximate the ground-sampling distance of each image. Pixel motion could then be converted into metres.
The displacement was rotated into a north–east reference frame using the accumulated yaw estimate. Successive motion estimates were integrated to produce a continuous local trajectory.
This method was fast enough to process image sequences at a nominal rate of 10 Hz, but because each estimate depended on the previous one, errors accumulated over time.

<img src="/images/SIFT_error.png" alt="Vision-based GPS-denied navigation architecture" style="width: 100%; max-width: 950px; border-radius: 10px; margin: 1.5rem 0;">

Combining Absolute and Relative Localization
Absolute and relative localization had complementary strengths.
The relative estimator produced frequent updates and captured the short-term motion of the UAV. However, its trajectory gradually drifted.
The absolute estimator did not accumulate the same type of drift because it referenced the satellite basemap directly. However, it was computationally expensive and could not produce a new position at the same rate as the relative estimator.
To combine them, the two branches were executed asynchronously.
The Relative Visual Localization loop continued processing incoming images and updating the trajectory. At the same time, the Absolute Visual Localization algorithm operated in a separate worker thread on the most recent available frame.
When an absolute estimate became available, it was not automatically assumed to correspond to the UAV’s current position. The estimate belonged to an earlier image that had already passed through the pipeline.
The system therefore stored a history of previous relative-localization states. Each delayed absolute result was associated with the history entry corresponding to the frame from which it had been calculated.
The difference between the absolute position and the relative estimate at that historical frame was used to calculate a north–east correction. This correction was then propagated through the stored trajectory and applied to the current position.
Very large corrections were rejected to reduce the effect of clearly incorrect absolute matches.
This approach allowed the slower absolute estimator to correct drift in the faster relative trajectory while accounting for the frame on which the absolute estimate had originally been calculated.

## Kalman-Filter State Estimation
After generating the visual-position estimates, I implemented a linear Kalman filter to combine them with inertial and barometric measurements and produce a smoother, continuous navigation state.
During the prediction stage, acceleration measurements from the simulated IMU were used as control inputs. Because the accelerometer measurements were initially expressed in the UAV body frame, the current roll, pitch, and yaw were used to transform them into the NED frame. Gravity was then removed before the acceleration was passed to the filter. The kinematic model propagated both position and velocity using the measured acceleration.
When a recent visual-navigation measurement was available, it was used to correct the predicted position. Barometric pressure was independently converted into altitude and used to constrain the vertical position. During development, simulated GPS was retained as an initialization and fallback measurement when no sufficiently recent visual estimate was available; it was not intended to be the primary source during GPS-denied operation.
The filter output contained the estimated three-dimensional position and velocity. The local NED position was then converted back into latitude, longitude, and altitude using the initial geographic reference. This fused geographic estimate was stored in shared memory and transmitted to ArduPilot through MAVLink as an external GPS input.
The Kalman filter reduced short-term measurement noise and provided a continuous state estimate between visual-position updates. However, it did not completely solve the main real-time problem. The absolute visual-localization measurements could arrive after the UAV had already moved, while the filter treated accepted measurements as observations of the current state. Consequently, delayed visual updates could create inconsistencies in the estimated position and contribute to instability when the output was used as a direct GPS replacement in the ArduPilot control loop.

## ArduPilot Integration
The final objective was not simply to display the estimated trajectory.
The visual position was intended to replace GPS inside an ArduPilot software-in-the-loop simulation.
AirSim generated the simulated vehicle motion, camera images, and other sensor data. The visual-localization pipeline processed the camera images and generated an estimated geographic position. This estimate was then intended to return to ArduPilot as an external position measurement.
ArduPilot could then use the visual estimate for navigation and vehicle control instead of relying on the simulated GPS output.
This closed-loop integration was the most demanding part of the project because navigation performance depends on more than the accuracy of an isolated position estimate. The flight controller also depends on the timing, update rate, consistency, and uncertainty of every measurement it receives.
A position estimate can be geographically accurate and still destabilize the vehicle if it arrives too late.
Main Challenge: Delayed Position Estimates
The localization algorithms worked well enough to identify the UAV’s position and generate a visually corrected trajectory.
The principal limitation appeared when the position estimates were introduced into the real-time control loop.
Absolute Visual Localization required several computational stages:
-	neural-network feature extraction;
-	parent-tile retrieval;
-	subtile retrieval;
-	detailed feature matching;
-	homography estimation;
-	geographic-coordinate conversion.

By the time this sequence was completed, the UAV had already moved away from the position shown in the processed image.
The returned coordinate was therefore an estimate of the UAV’s past position.
I attempted to compensate for this by associating every absolute result with its original image frame and applying its correction to the stored history of relative estimates. This improved the internal consistency of the fused trajectory.
However, reliably using the resulting estimates as a direct GPS replacement in ArduPilot remained difficult. The delayed corrections caused inconsistencies between the navigation estimate and the vehicle’s actual simulated state.
When these delayed measurements were introduced into the flight-control loop, the UAV response became unstable.
The project therefore demonstrated that solving visual localization offline is not the same as solving real-time visual navigation. In a closed-loop system, measurement delay must be treated as part of the estimator design rather than as a secondary implementation detail.
## Results and Outcome

The completed pipeline and the final closed-loop experiment revealed the main unresolved limitation: the latency of absolute localization prevented the position output from serving as a stable real-time replacement for GPS in ArduPilot.
Although the full navigation objective was not achieved, this limitation was technically significant. It identified the point at which the system transitioned from a successful computer-vision pipeline into an unstable real-time control system.
changed how I viewed localization systems.
## Future Improvements
The most important future improvement would be a state estimator designed explicitly for delayed and asynchronous measurements.
Rather than applying corrections as simple offsets, the system could use an Extended Kalman Filter, factor graph, or fixed-lag smoother that stores previous vehicle states and updates the correct historical state when a delayed visual measurement arrives.


