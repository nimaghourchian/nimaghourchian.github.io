---
permalink: /
title: "About"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

<style>

.page__content p.about-intro {
  font-size: 1rem !important;
  line-height: 1.65;
}
  
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
  width: 1.6em !important;
  height: 1.6em !important;
  margin: 0 !important;
  border-radius: 0 !important;
  object-fit: contain !important;
  flex: 0 0 1.4em !important;
}


/* Professional Experience card */
.experience-card {
  display: flex;
  align-items: center;
  gap: 2rem;
  width: 100%;
  padding: 1.25rem;
  margin-bottom: 1.8rem;

  background: #ffffff;
  border: 1px solid #d9e1ea;
  border-radius: 10px;
  box-shadow: none;
}

.experience-images {
  position: relative;
  flex: 0 0 240px;
  margin: 0 0 1.2rem 0;
}

.experience-main-image {
  display: block;
  width: 240px !important;
  height: 160px !important;
  margin: 0 !important;

  object-fit: cover;
  border-radius: 7px;
}

.experience-overlap-image {
  position: absolute;
  right: -22px;
  bottom: -24px;

  width: 100px !important;
  height: 72px !important;
  margin: 0 !important;

  object-fit: cover;
  background: #ffffff;
  border: 4px solid #ffffff;
  border-radius: 7px;
  box-shadow: 0 5px 14px rgba(0, 0, 0, 0.2);
}

.experience-content {
  flex: 1;
  min-width: 0;
  padding-left: 0.25rem;
}

.experience-content h3 {
  margin: 0 0 0.45rem;
  color: #24364a;
  font-size: 1.1rem;
  line-height: 1.25;
  font-weight: 700;
}

.experience-content p {
  margin: 0;
  color: #4b5563;
  font-size: 0.92rem;
  line-height: 1.4;
  font-weight: 600;
}

@media (max-width: 800px) {
  .experience-card {
    display: block;
    padding: 1rem;
  }

  .experience-images {
    width: calc(100% - 18px);
    max-width: 500px;
    margin: 0 18px 2.8rem 0;
  }

  .experience-main-image {
    width: 100% !important;
    height: auto !important;
    aspect-ratio: 3 / 2;
  }

  .experience-overlap-image {
    right: -18px;
    bottom: -32px;
    width: 36% !important;
    height: auto !important;
    aspect-ratio: 4 / 3;
  }

  .experience-content {
    padding-left: 0;
  }
}

</style>

<p class="about-intro">
  Hello, I am a mechanical engineering graduate interested in the control of
  complex autonomous and multi-agent systems. My specific interests include
  adaptive control, state estimation, nonlinear dynamics, and sensor fusion.
</p>

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


<h2 id="professional-experience">Professional Experience</h2>

<div class="experience-card">
  <div class="experience-images">
    <img
      class="experience-main-image"
      src="/images/drone-work.jpg"
      alt="Working on the SpaceOmid agricultural drone"
    >

    <img
      class="experience-overlap-image"
      src="/images/agri-drone.jpg"
      alt="SpaceOmid agricultural drone"
    >
  </div>

 <div class="experience-content">
  <h3>SpaceOmid</h3>

  <div class="highlight-meta">
    Flight Control &amp; Simulation Engineer
  </div>
</div>
</div>
