---
title: "About"
permalink: /about/
layout: single
author_profile: false
classes: wide
toc: false
header:
  overlay_image: /assets/images/post-banner.jpg
  overlay_filter: "linear-gradient(90deg, rgba(12, 28, 48, 0.8) 0%, rgba(12, 28, 48, 0.4) 55%, rgba(12, 28, 48, 0.05) 100%)"
---

<div class="about-card">
  <img class="about-card__avatar" src="{{ site.author.avatar | relative_url }}" alt="{{ site.author.name }}">
  <div class="about-card__info">
    <h2 class="about-card__name">{{ site.author.name }}</h2>
    <p class="about-card__bio">{{ site.author.bio }}</p>
    <div class="about-card__links">
      {% for link in site.author.links %}<a class="about-link" href="{{ link.url }}"><i class="{{ link.icon }}" aria-hidden="true"></i> {{ link.label }}</a>
      {% endfor %}
    </div>
  </div>
</div>

<p class="research-lead">I'm Chengdong Weng, a high school student in Beijing, China. I'm interested in machine learning, engineering, and building things that make useful technology cheaper and more accessible.</p>

<h2 class="research-heading">What this blog is about</h2>

<p>This blog is my research notebook. Right now I'm working on a question that sits between hardware and machine learning:</p>

<blockquote class="about-question">How much sensor resolution does sleep-posture classification actually need?</blockquote>

<p>High-resolution pressure mats can tell whether a person is lying on their back or side, which matters for pressure-ulcer prevention and patient monitoring, but the good ones are expensive. I'm studying how far you can cut the number of sensors, and when the coverage of the mat matters more than the density of sensors, before the classification breaks.</p>

<div class="method-note">
  <p>I'm doing this project under the mentorship of a postdoc researcher, and I write here to keep a public record of the work: the experiments, the dead ends, the results, and what I learn along the way.</p>
</div>

<h2 class="research-heading">Where to start</h2>

<div class="about-nav">
  <a class="about-nav__card" href="/blog/welcome-and-why-im-writing-this/">
    <span class="axis-card__tag">First post</span>
    <strong>Start here</strong>
    <span>Why I'm writing all of this down.</span>
  </a>
  <a class="about-nav__card" href="/research/">
    <span class="axis-card__tag">Overview</span>
    <strong>Research</strong>
    <span>The question and the main findings.</span>
  </a>
  <a class="about-nav__card" href="/posts/">
    <span class="axis-card__tag">Archive</span>
    <strong>All posts</strong>
    <span>Every post, in order.</span>
  </a>
</div>

<div class="research-footer">
  <p><em>You can find my code and projects on <a href="https://github.com/ChengdongWeng">GitHub</a>.</em></p>
</div>
