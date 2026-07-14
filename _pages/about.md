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
  gap: 1.6rem;
  align-items: flex-start;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 1.3rem;
  margin-bottom: 1.6rem;
  background: #ffffff;
  box-shadow: 0 4px 18px rgba(0, 0, 0, 0.04);
}

.highlight-card img,
.highlight-card video {
  width: 210px;
  height: 140px;
  object-fit: cover;
  border-radius: 8px;
  flex-shrink: 0;
}

.highlight-content h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
  color: #24364a;
  font-size: 1.25rem;
}

.highlight-content p {
  margin-bottom: 0.8rem;
  line-height: 1.55;
}

.highlight-meta {
  background: #f7f8fb;
  border-left: 4px solid #6177f2;
  padding: 0.65rem 0.85rem;
  border-radius: 7px;
  margin-bottom: 0.9rem;
  font-weight: 600;
  color: #344054;
}

.highlight-button {
  display: inline-block;
  padding: 0.45rem 0.8rem;
  border: 1px solid #d0d7de;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 700;
}

.highlight-button:hover {
  background: #f3f4f6;
}

@media (max-width: 700px) {
  .highlight-card {
    display: block;
  }

  .highlight-card img,
  .highlight-card video {
    width: 100%;
    height: auto;
    margin-bottom: 1rem;
  }
}
</style>

Hello, I am a mechanical engineering graduate interested in the control of complex autonomous and multi-agent systems. My interests include adaptive control, state estimation, nonlinear dynamics, and sensor fusion.

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
