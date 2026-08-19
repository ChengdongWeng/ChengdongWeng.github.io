---
title: "Research"
permalink: /research/
author_profile: true
toc: true
---

## How much resolution does sleep-posture classification need?

High-resolution pressure mats can classify how a person is lying in bed, which matters for pressure-ulcer prevention and patient monitoring. But high-resolution medical mats are expensive. This project asks a sharper question: **what is the minimum resolution posture classification actually needs, and does "resolution" mean sensor density or coverage area?**

I separate two things that are usually conflated:

- **Density** — fewer sensors over the same area (downsampling).
- **Coverage** — the same sensors over a smaller area (cropping).

### Key findings so far

- Classification is **highly robust to lower density**: cutting the sensor count by 64x still keeps macro-F1 above 0.92.
- It is **much more fragile to reduced coverage**: cropping the mat to a quarter of its area collapses convolutional models, especially for the side-lying classes.
- **Coverage matters more than density** — a coarse full-length mat beats a fine torso-only patch at the same sensor budget.

All experiments use strict subject-independent (leave-one-subject-out) validation across seven model families, so the numbers reflect performance on genuinely new users rather than leaked data.

*This page will be updated with figures, the full write-up, and code as the project develops. Code lives on [GitHub](https://github.com/ChengdongWeng).*
