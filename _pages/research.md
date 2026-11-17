---
title: "Research"
permalink: /research/
layout: single
author_profile: false
classes: wide
toc: false
tagline: "How much resolution does sleep-posture classification need?"
header:
  overlay_image: /assets/images/research-banner.jpg
  overlay_filter: "linear-gradient(90deg, rgba(12, 28, 48, 0.8) 0%, rgba(12, 28, 48, 0.4) 55%, rgba(12, 28, 48, 0.05) 100%)"
  actions:
    - label: "Read the research blog"
      url: "/posts/"
---

<p class="research-lead">High-resolution pressure mats can classify how a person is lying in bed, which matters for pressure-ulcer prevention and patient monitoring. But high-resolution medical mats are expensive. This project asks a sharper question: <strong>what is the minimum resolution posture classification actually needs, and does "resolution" mean sensor density or coverage area?</strong></p>

<h2 class="research-heading">Two kinds of resolution</h2>

<p>I separate two things that are usually conflated:</p>

<div class="axis-cards">
  <div class="axis-card">
    <span class="axis-card__tag">Axis 1</span>
    <h3>Density</h3>
    <p>Fewer sensors over the same area (downsampling).</p>
  </div>
  <div class="axis-card axis-card--coverage">
    <span class="axis-card__tag">Axis 2</span>
    <h3>Coverage</h3>
    <p>The same sensors over a smaller area (cropping).</p>
  </div>
</div>

<figure class="research-figure research-figure--narrow">
  <img src="/assets/images/research-example-frames.png" alt="Example pressure frames from PMD and PoPu Tactilus at four resolutions, with the half and quarter crop areas marked in orange.">
  <figcaption>Example frames from PMD (top) and PoPu's Tactilus mat (bottom). Moving right, neighboring sensors are averaged together, so the mat keeps its size but has fewer sensors. The orange lines mark the half and quarter crops, which keep the sensor spacing but cover less of the body.</figcaption>
</figure>

<h2 class="research-heading">Key findings so far</h2>

<ol class="findings">
  <li><strong>Far fewer sensors are enough</strong>: cutting the sensor count to about 1/16 (128 sensors on PMD, 96 on PoPu's Tactilus mat) causes no significant loss for nearly all models, and full resolution is rarely the best setting.</li>
  <li><strong>At a fixed sensor budget, keep the full body length</strong>: on PoPu, a sparse full-length layout beat a dense middle-only layout for 6 of 7 models (p &lt; 0.001). On PMD the two layouts were not significantly different.</li>
  <li><strong>A 72-cell mat under the mattress can match a 1,728-sensor mat</strong> with classical models, but drops to near chance once only one column is left across the bed.</li>
</ol>

<figure class="research-figure">
  <img src="/assets/images/research-sensor-count.png" alt="Macro-F1 against number of sensors for PMD, PoPu Tactilus and PoPu SensoMatt.">
  <figcaption>Macro-F1 against the number of sensors, averaged over the seven models. The shaded band is the range across models. Left: all three mats. Right: a closer look at PMD and Tactilus, with the cropped mats shown as hollow markers.</figcaption>
</figure>

<figure class="research-figure">
  <img src="/assets/images/research-seven-models.png" alt="Macro-F1 of each of the seven models against number of sensors on PMD, PoPu Tactilus and PoPu SensoMatt.">
  <figcaption>The same comparison for each of the seven models separately.</figcaption>
</figure>

<div class="method-note">
  <p>All experiments use strict subject-independent validation (leave-one-subject-out on PMD, five folds split by volunteer on PoPu) across seven model families, so the numbers reflect performance on genuinely new users rather than leaked data.</p>
</div>

<div class="research-footer">
  <p><em>This page will be updated with figures, the full write-up, and code as the project develops. Code lives on <a href="https://github.com/ChengdongWeng">GitHub</a>.</em></p>
  <a class="btn btn--primary" href="https://github.com/ChengdongWeng">GitHub</a>
</div>
