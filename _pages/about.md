---
permalink: /
title: "About"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

<style>
.highlight-card {
  display: flex;
  gap: 1.5rem;
  align-items: flex-start;
  border: 1px solid #d9e1ea;
  border-radius: 14px;
  padding: 1.4rem 1.6rem;
  margin-bottom: 1.8rem;
  background: #ffffff;
  box-shadow: none;
  max-width: 1280px;
}

.highlight-card img,
.highlight-card video {
  width: 220px;
  height: 150px;
  object-fit: cover;
  border-radius: 8px;
  flex-shrink: 0;
  margin-top: 0.2rem;
}

.highlight-content {
  flex: 1;
}

.highlight-content h3 {
  margin-top: 0;
  margin-bottom: 0.45rem;
  color: #24364a;
  font-size: 1.15rem;
  line-height: 1.25;
  font-weight: 700;
}

.highlight-content p {
  margin-top: 0;
  margin-bottom: 0.9rem;
  line-height: 1.55;
  color: #4b5563;
  font-size: 0.98rem;
}

.highlight-meta {
  background: #f7f8fb;
  border-left: 4px solid #5b74f2;
  padding: 0.7rem 0.95rem;
  border-radius: 8px;
  margin-bottom: 0.95rem;
  font-weight: 600;
  color: #344054;
  font-size: 0.96rem;
  line-height: 1.45;
}

.highlight-button {
  display: inline-block;
  padding: 0.42rem 0.82rem;
  border: 1px solid #d0d7de;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 700;
  font-size: 0.95rem;
  color: #3b82c4 !important;
  background: #ffffff;
}

.highlight-button:hover {
  background: #f3f4f6;
  text-decoration: none;
}

/* Optional: make the first card have a blue outline like the example */
.highlight-card:first-of-type {
  border-color: #59aaf7;
}

@media (max-width: 800px) {
  .highlight-card {
    display: block;
    padding: 1.2rem;
  }

  .highlight-card img,
  .highlight-card video {
    width: 100%;
    height: auto;
    margin-bottom: 1rem;
  }
}
</style>

Hello, I am a mechanical engineering student interested in the control of complex autonomous and multi-agent systems. My specific interests include adaptive control, state estimation, nonlinear dynamics, and sensor fusion.

Email: [nima.ghourchian01@gmail.com](mailto:nima.ghourchian01@gmail.com)

## Selected Projects

<div class="highlight-card">
  <img src="/images/cubesat-team.jpg" alt="3U CubeSat ADCS project">

  <div class="highlight-content">
    <h3>3U CubeSat Attitude Determination and Control System</h3>

    <p>
      ADCS development for a national 3U CubeSat competition, including B-dot detumbling,
      quaternion-feedback attitude control, orbital day/night sensor-selection logic,
      and Simulink-based validation.
    </p>

    <div class="highlight-meta">
      🛰 National 3U CubeSat Competition — Top 4 of 52 teams
    </div>

    <a class="highlight-button" href="/projects/cubesat-adcs/">Project Details</a>
  </div>
</div>

<div class="highlight-card">
  <video autoplay muted loop playsinline preload="metadata">
    <source src="/videos/gps-denied-navigation.mp4" type="video/mp4">
  </video>

  <div class="highlight-content">
    <h3>Vision-Based GPS-Denied Navigation</h3>

    <p>
      Vision-based UAV localization pipeline using satellite–UAV image matching,
      visual odometry, homography-based geographic estimation, and Kalman-filter-based
      state estimation for GPS-denied navigation.
    </p>

    <div class="highlight-meta">
      🚁 Bachelor’s Final Project — Solo Project
    </div>

    <a class="highlight-button" href="/projects/gps-denied-navigation/">Project Details</a>
  </div>
</div>
