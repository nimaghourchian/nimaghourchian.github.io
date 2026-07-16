---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: false
---

<style>
.archive {
  float: none !important;
  width: 100% !important;
  padding-left: 0 !important;
  margin-left: auto !important;
  margin-right: auto !important;
}

.archive .page__title {
  width: 100%;
  max-width: 1650px;
  margin-left: auto;
  margin-right: auto;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 620px));
  justify-content: center;
  column-gap: clamp(3rem, 9vw, 14rem);
  row-gap: 2.4rem;
  width: 100%;
  max-width: 1450px;
  margin: 1.5rem auto 0;
}

.project-card {
  background: #ffffff;
  border: 1px solid #eeeeee;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 8px 28px rgba(0, 0, 0, 0.08);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 14px 34px rgba(0, 0, 0, 0.13);
}

.project-image-wrapper {
  position: relative;
  width: 100%;
  aspect-ratio: 16 / 9;
  overflow: hidden;
}

.project-image-wrapper img,
.project-image-wrapper video {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.project-year-badge {
  position: absolute;
  top: 0;
  right: 0;
  padding: 0.7rem 0.9rem;
  border-bottom-left-radius: 14px;
  background: #222222;
  color: #ffffff;
  font-size: 0.82rem;
  font-weight: 700;
  white-space: nowrap;
}

.project-content {
  padding: 1.5rem;
}

.project-title {
  margin-top: 0;
  margin-bottom: 1rem;
  font-size: 1.35rem;
  line-height: 1.35;
  font-weight: 700;
}

.project-title a {
  color: #24364a;
  text-decoration: none;
}

.project-title a:hover {
  color: #4f68e8;
}

.project-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  padding: 0.8rem 1rem;
  margin-bottom: 1.4rem;
  border-left: 4px solid #6177f2;
  border-radius: 8px;
  background: #f7f8fb;
  color: #344054;
  font-size: 0.92rem;
  font-weight: 600;
}

.project-meta span {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
}

.project-button {
  display: block;
  padding: 0.85rem 1rem;
  border-radius: 8px;
  background: #6177f2;
  color: #ffffff !important;
  text-align: center;
  text-decoration: none !important;
  font-weight: 700;
  transition: background 0.2s ease;
}

.project-button:hover {
  background: #4f63dc;
}

.project-button,
.project-button:link,
.project-button:visited,
.project-button:hover,
.project-button:focus,
.project-button:active {
  text-decoration: none !important;
  border-bottom: none !important;
  box-shadow: none !important;
  background-image: none !important;
}

@media (max-width: 900px) {
  .projects-grid {
    grid-template-columns: 1fr;
    max-width: 700px;
  }

  .project-image-wrapper {
    height: 210px;
  }
}
</style>

<div class="projects-grid">

  <div class="project-card">
    <a href="/projects/cubesat-adcs/">
      <div class="project-image-wrapper">
        <img src="/images/cubesat-team.jpg" alt="3U CubeSat ADCS team">
        <div class="project-year-badge">Jan 2024 — Present</div>
      </div>
    </a>

    <div class="project-content">
      <h2 class="project-title">
        <a href="/projects/cubesat-adcs/">Attitude Determination and Control System</a>
      </h2>

      <div class="project-meta">
        
        <span>🛰 National 3U CubeSat Competition (Qsat)</span>
      </div>

      <a class="project-button" href="/projects/cubesat-adcs/">Project Details</a>
    </div>
  </div>

<div class="project-card">
  <a href="/projects/gps-denied-navigation/">
    <div class="project-image-wrapper">
      <video autoplay muted loop playsinline preload="metadata">
        <source src="/videos/gps-denied-navigation.mp4" type="video/mp4">
      </video>
      <div class="project-year-badge">Jun 2025 — Jan 2026</div>
    </div>
  </a>
  

    <div class="project-content">
      <h2 class="project-title">
        <a href="/projects/gps-denied-navigation/">Vision-Based GPS-Denied Navigation</a>
      </h2>

      <div class="project-meta">
        <span>🚁 Bachelor’s Final Project</span>
      </div>

      <a class="project-button" href="/projects/gps-denied-navigation/">Project Details</a>
    </div>
  </div>

</div>
