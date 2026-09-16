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

.cubesat-news-link {
  display: inline-block;
  margin: 0.35rem 0 1.5rem;
  padding: 0.45rem 0.8rem;
  color: #2486c7 !important;
  background: #ffffff;
  border: 1px solid #d0d7de !important;
  border-bottom: 1px solid #d0d7de !important;
  border-radius: 6px;
  box-shadow: none !important;
  background-image: none !important;
  font-size: 0.84rem;
  font-weight: 700;
  line-height: 1.4;
  text-decoration: none !important;
}

.cubesat-news-link:hover,
.cubesat-news-link:focus,
.cubesat-news-link:active,
.cubesat-news-link:visited {
  color: #2486c7 !important;
  border-bottom: 1px solid #d0d7de !important;
  box-shadow: none !important;
  background-image: none !important;
  text-decoration: none !important;
}

.cubesat-news-link:hover {
  color: #176fa8 !important;
  background: #f3f6f9;
  border-color: #59aaf7 !important;
}

.cubesat-team-photo {
  display: block;
  width: 100%;
  max-width: 850px;
  height: auto;
  margin: 0 auto 1.5rem;
  border-radius: 10px;
}

/* Keep model screenshots legible at the full content width. */
.cubesat-model {
  margin: 1.5rem 0 2rem;
}
.cubesat-model-image {
  display: block;
  border: 1px solid var(--global-border-color, #d0d7de);
  border-radius: 8px;
  background: #fff;
}
.cubesat-model-image:focus-visible {
  outline: 3px solid #2486c7;
  outline-offset: 4px;
}
.cubesat-model-image img {
  display: block;
  width: 100%;
  height: auto;
  margin: 0;
  border-radius: 8px;
}
.cubesat-model figcaption {
  margin-top: 0.65rem;
  font-size: 0.9rem;
  line-height: 1.6;
  text-align: left;
}
.cubesat-model figcaption strong {
  display: block;
  color: var(--global-text-color, #333);
}
.cubesat-model-link {
  display: inline-block;
  margin-top: 0.4rem;
}
.cubesat-sil {
  margin: 0 0 2rem;
  padding: 0.85rem 1rem;
  border: 1px solid var(--global-border-color, #d0d7de);
  border-radius: 8px;
}
.cubesat-sil summary {
  cursor: pointer;
  font-weight: 700;
  line-height: 1.5;
}
.cubesat-sil summary:focus-visible {
  outline: 3px solid #2486c7;
  outline-offset: 4px;
}
.cubesat-sil .cubesat-model {
  margin: 1rem 0 0;
}
</style>

This competition gave participating teams the freedom to define their own CubeSat missions and design the spacecraft around the resulting requirements. After evaluating several mission concepts, our team developed Cubisa, a 3U CubeSat intended to demonstrate technologies relevant to tether-based space-debris removal.

The spacecraft consisted of the main satellite, named Q, and a detachable module, named Bisa, representing a target object. The proposed mission involved stabilizing the spacecraft after orbital injection, deploying Bisa using an inter-satellite tether, observing its relative motion through onboard imaging, retrieving and reconnecting it, reorienting the combined spacecraft, and finally deploying a drag sail to accelerate orbital decay.

Our design progressed through the conceptual and detailed design stages, ultimately placing among the top four of 52 teams nationwide and receiving funding to develop an engineering prototype.

[View the competition announcement and results (Persian) ↗](https://snn.ir/fa/news/1191297/%D8%AD%D9%85%D8%A7%DB%8C%D8%AA-%DB%B6%DB%B0%DB%B0-%D9%85%DB%8C%D9%84%DB%8C%D9%88%D9%86-%D8%AA%D9%88%D9%85%D8%A7%D9%86%DB%8C-%D8%A7%D8%B2-%D8%AA%DB%8C%D9%85%E2%80%8C%D9%87%D8%A7%DB%8C-%D8%A8%D8%B1%D8%AA%D8%B1-%D8%B1%D9%88%DB%8C%D8%AF%D8%A7%D8%AF-%D9%81%D9%86%D8%A7%D9%88%D8%B1%D8%A7%D9%86%D9%87-qsat){: .cubesat-news-link }

![Cubisa team during the national QSat competition](/images/cubesat-team.jpg){: .cubesat-team-photo }

My role as a member of the Attitude Determination and Control System team involved translating the mission profile into ADCS requirements, researching, selecting and implementing the control architecture, developing the orbital and attitude dynamics simulation, defining reference frames and coordinate transformations, implementing and tuning the attitude controller, designing orbital day/night sensor-selection logic, combining sensor measurements to reduce noise and drift, and validating the system through software-in-the-loop and processor-in-the-loop testing.




<figure class="cubesat-model">
  <a class="cubesat-model-image" href="{{ '/images/Orbital_Model.jpg' | relative_url }}" target="_blank" rel="noopener" aria-label="Open the orbital and environmental model at full resolution in a new tab">
    <img src="{{ '/images/Orbital_Model.jpg' | relative_url }}" alt="Simulink orbital model showing the propagator, atmospheric drag, Sun and eclipse models, geomagnetic field, and reference-frame transformations" width="2048" height="885" loading="lazy" decoding="async">

  <figcaption>
    <strong>Orbital and Environmental Model</strong>
    Orbital propagation with atmospheric drag, Sun-vector and eclipse calculations, geomagnetic-field modelling, and reference-frame transformations.

  </figcaption>
</figure>




  <figure class="cubesat-model">
    <a class="cubesat-model-image" href="{{ '/images/SIL.jpg' | relative_url }}" target="_blank" rel="noopener" aria-label="Open the full software-in-the-loop model at full resolution in a new tab">
      <img src="{{ '/images/SIL.jpg' | relative_url }}" alt="Full Simulink SIL model showing the feedback connections between attitude commands, control, magnetic actuation, attitude dynamics, quaternion propagation, and sensor fusion" width="2048" height="1384" loading="lazy" decoding="async">
    </a>
    <figcaption>
      The integrated simulation connects the controller, actuator torque, attitude equations of motion, quaternion propagation, and sensor-fusion feedback.
    </figcaption>
  </figure>
</details>

Although the circumstances in the country slowed down our progress repeatedly and caused HIL testing to remain unfinished, This project gave me a practical experience with the development process of a CubeSat's control subsystem, from interpreting mission requirements and studying algorithms to mathematical modelling, sensor management, controller tuning, simulation, and embedded integration.

More importantly, it taught me that developing a control system is not only a matter of implementing equations from a paper. Every theoretical decision must remain consistent with the CubeSat's mission, coordinate conventions, sensor usage, actuator constraints, limitations of computational hardware, and validation strategy.

