---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: false
---

<style>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(280px, 1fr));
  gap: 2.4rem;
  margin-top: 1.5rem;
}

.project-card {
  background: #ffffff;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 8px 28px rgba(0, 0, 0, 0.08);
  border: 1px solid #eeeeee;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 14px 34px rgba(0, 0, 0, 0.13);
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

.project-image-wrapper {
  position: relative;
  width: 100%;
  height: 220px;
  overflow: hidden;
}

.project-image-wrapper img,
.project-image-wrapper video {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.project-year-badge {
  position: absolute;
  top: 0;
  right: 0;
  background: #222;
  color: #ffffff;
  font-weight: 700;
  font-size: 0.95rem;
  padding: 0.75rem 1rem;
  border-bottom-left-radius: 14px;
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
  background: #f7f8fb;
  border-left: 4px solid #6177f2;
  border-radius: 8px;
  padding: 0.8rem 1rem;
  margin-bottom: 1.4rem;
  color: #6177f2;
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
  text-align: center;
  background: #6177f2;
  color: #ffffff !important;
  text-decoration: none;
  font-weight: 700;
  padding: 0.85rem 1rem;
  border-radius: 8px;
  transition: background 0.2s ease;
}

.project-button:hover {
  background: #4f63dc;
}

@media (max-width: 900px) {
  .projects-grid {
    grid-template-columns: 1fr;
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
        <div class="project-year-badge">2025</div>
      </div>
    </a>

    <div class="project-content">
      <h2 class="project-title">
        <a href="/projects/cubesat-adcs/">Attitude Determination and Control System</a>
      </h2>

      <div class="project-meta">
        <span><i class="fas fa-calendar" aria-hidden="true"></i>Jan 2025 — Present</span>
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
      <div class="project-year-badge">2026</div>
    </div>
  </a>
  

    <div class="project-content">
      <h2 class="project-title">
        <a href="/projects/gps-denied-navigation/">Vision-Based GPS-Denied Navigation</a>
      </h2>

      <div class="project-meta">
        <span><i class="fas fa-calendar" aria-hidden="true"></i>Jun 2025 — Jan 2026</span>
        <span>🏛 Bachelor’s Final Project</span>
      </div>

      <a class="project-button" href="/projects/gps-denied-navigation/">Project Details</a>
    </div>
  </div>

</div>
