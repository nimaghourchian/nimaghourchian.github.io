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
  gap: 1.4rem;
  align-items: flex-start;
  border: 1px solid #d9e1ea;
  border-radius: 10px;
  padding: 1.05rem 1.25rem;
  margin-bottom: 1.4rem;
  background: #ffffff;
  box-shadow: none;
  width: 100%;
}

.highlight-card img,
.highlight-card video {
  width: 170px;
  height: 135px;
  object-fit: cover;
  border-radius: 6px;
  flex-shrink: 0;
  margin-top: 0.1rem;
}

.highlight-content {
  flex: 1;
  min-width: 0;
}

.highlight-content h3 {
  margin-top: 0;
  margin-bottom: 0.75rem;
  color: #24364a;
  font-size: 1rem;
  line-height: 1.25;
  font-weight: 700;
}

.highlight-content p {
  margin-top: 0;
  margin-bottom: 0.65rem;
  line-height: 1.45;
  color: #4b5563;
  font-size: 0.88rem;
}

.highlight-meta {
  background: #f7f8fb;
  border-left: 4px solid #5b74f2;
  padding: 0.5rem 0.75rem;
  border-radius: 6px;
  margin-bottom: 0.7rem;
  font-weight: 600;
  color: #344054;
  font-size: 0.82rem;
  line-height: 1.35;
}

.highlight-button {
  display: inline-block;
  padding: 0.32rem 0.65rem;
  border: 1px solid #d0d7de;
  border-radius: 5px;
  text-decoration: none !important;
  font-weight: 700;
  font-size: 0.82rem;
  color: #2486c7 !important;
  background: #ffffff;
}

.highlight-button:hover {
  background: #f3f4f6;
  text-decoration: none !important;
}

.highlight-card:hover {
  border-color: #59aaf7;
  box-shadow: 0 6px 18px rgba(89, 170, 247, 0.12);
}

@media (max-width: 800px) {
  .highlight-card {
    display: block;
    padding: 1rem;
  }

  .highlight-card img,
  .highlight-card video {
    width: 100%;
    height: auto;
    margin-bottom: 1rem;
  }
}

/* Kill the theme-forced underline on Project Details buttons */
.highlight-button,
.highlight-button:link,
.highlight-button:visited,
.highlight-button:hover,
.highlight-button:focus,
.highlight-button:active {
  text-decoration: none !important;
  border: 1px solid #d0d7de !important;
  border-bottom: 1px solid #d0d7de !important;
  box-shadow: none !important;
  background-image: none !important;
}

  .highlight-card .highlight-meta img.drone-icon {
  width: 1.4em !important;
  height: 1.4em !important;
  margin: 0 !important;
  border-radius: 0 !important;
  object-fit: contain !important;
  flex: 0 0 1.4em !important;
}
</style>

Hello, I am a mechanical engineering student interested in the control of complex autonomous and multi-agent systems. My specific interests include adaptive control, state estimation, nonlinear dynamics, and sensor fusion.


## Selected Projects

<div class="highlight-card">
  <img src="/images/cubesat-team.jpg" alt="3U CubeSat ADCS project">

  <div class="highlight-content">
    <h3> Attitude Determination and Control System</h3>

    

    <div class="highlight-meta">
      🛰 National 3U CubeSat Competition (Qsat)
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



    <div class="highlight-meta">
  <img src="/images/drone-icon.png" alt="" class="drone-icon">
  Bachelor’s Final Project
</div>

    <a class="highlight-button" href="/projects/gps-denied-navigation/">Project Details</a>
  </div>
</div>
