---
layout: single
title: "Attitude Determination and Control System"
permalink: /projects/cubesat-adcs/
author_profile: false
---

<style>
.page__content {
  padding-top: 1.5rem;
}

.news-source-link {
  display: inline-block;
  margin: 0.35rem 0 1.5rem;
  padding: 0.45rem 0.8rem;
  color: #2486c7 !important;
  background: #ffffff;
  border: 1px solid #d0d7de;
  border-radius: 6px;
  font-size: 0.84rem;
  font-weight: 700;
  line-height: 1.4;
  text-decoration: none !important;
}

.news-source-link:link,
.news-source-link:visited,
.news-source-link:hover,
.news-source-link:focus,
.news-source-link:active {
  text-decoration: none !important;
  border-bottom: 1px solid #d0d7de !important;
  box-shadow: none !important;
  background-image: none !important;
}

.news-source-link:hover {
  color: #176fa8 !important;
  background: #f3f6f9;
  border-color: #59aaf7 !important;
}
</style>

This competition gave participating teams the freedom to define their own CubeSat missions and design the spacecraft around the resulting requirements. After evaluating several mission concepts, our team developed Cubisa, a 3U CubeSat intended to demonstrate technologies relevant to tether-based space-debris removal.

The spacecraft consisted of the main satellite, named Q, and a detachable module, named Bisa, representing a target object. The proposed mission involved stabilizing the spacecraft after orbital injection, deploying Bisa using an inter-satellite tether, observing its relative motion through onboard imaging, retrieving and reconnecting it, reorienting the combined spacecraft, and finally deploying a drag sail to accelerate orbital decay.

Our design progressed through the conceptual and detailed design stages, ultimately placing among the top four of 52 teams nationwide and receiving funding to develop an engineering prototype.

<a
  class="news-source-link"
  href="https://snn.ir/fa/news/1191297/%D8%AD%D9%85%D8%A7%DB%8C%D8%AA-%DB%B6%DB%B0%DB%B0-%D9%85%DB%8C%D9%84%DB%8C%D9%88%D9%86-%D8%AA%D9%88%D9%85%D8%A7%D9%86%DB%8C-%D8%A7%D8%B2-%D8%AA%DB%8C%D9%85%E2%80%8C%D9%87%D8%A7%DB%8C-%D8%A8%D8%B1%D8%AA%D8%B1-%D8%B1%D9%88%DB%8C%D8%AF%D8%A7%D8%AF-%D9%81%D9%86%D8%A7%D9%88%D8%B1%D8%A7%D9%86%D9%87-qsat"
  target="_blank"
  rel="noopener noreferrer"
>
  View the competition announcement and results (Persian) ↗
</a>

<img
  src="/images/cubesat-team.jpg"
  alt="Cubisa team during the national QSat competition"
  style="display:block; width:100%; max-width:850px; border-radius:10px; margin:0 auto 1.5rem;"
>

My role as a member of the Attitude Determination and Control System team involved translating the mission profile into ADCS requirements, researching and selecting the control architecture, developing the orbital and attitude-dynamics simulation, defining reference frames and coordinate transformations, implementing and tuning the attitude controller, designing orbital day/night sensor-selection logic, combining sensor measurements to reduce noise and drift, and validating the system through software-in-the-loop and processor-in-the-loop testing.

This project gave me experience with the complete development process of a spacecraft control subsystem—from interpreting mission requirements and studying candidate algorithms to mathematical modelling, sensor management, controller tuning, simulation, and embedded integration.

More importantly, it taught me that developing a control system is not merely a matter of implementing equations from a paper. Every theoretical decision must remain consistent with the spacecraft’s mission, coordinate conventions, sensor availability, actuator constraints, computational hardware, and validation strategy.
