---
title: "Why I killed my first research idea before it really started"
date: 2026-07-16
categories:
  - blog
tags:
  - research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

My research didn't start with pressure mats. It started with radar.

The first plan was pretty ambitious. I wanted to use a mmWave radar to sense sleep: breathing, sleep quality, and mostly sleep posture. The idea sounded great in my head. A little radar sits on your nightstand, uses no camera at all, and somehow just knows how you're lying in bed. I wrote a proposal, put together an outline, and read some papers on radar-based sensing.

I was really into it. And then my mentor talked me out of it, and honestly he was right.

What got to me a little is that he pointed at almost exactly the problems I'd noticed and then quietly ignored. So here's the honest list of why radar was the wrong first project for me.

The biggest one was data. For pressure-mat sleep sensing there are real datasets that other researchers have already released, so I can download them and start. For radar-based sleep posture, there's basically nothing usable out there. That means I wouldn't really be doing the research I wanted to do. I'd spend months just trying to collect data before I could even begin.

And collecting that data is not something I can do. To train a model you need labels, which means someone actually confirming "this person is on their left side right now" while they sleep. In practice that's a sleep lab, with real participants staying overnight and extra equipment to record the truth. That's a clinical setup. I'm a high school student. I can't run overnight human data collection, and I shouldn't pretend I can.

There was also the hardware. Radar means buying a development board, wiring it up, and tuning it. One rule I set for myself early on was that I wouldn't buy hardware unless there was a really clear reason. Radar broke that rule on the first day.

On top of that, the signal processing was mostly a black box to me. Getting from what the radar actually measures to something a model can use takes a lot of processing steps that I didn't really understand yet. I care about being able to explain what I do, all of it. With radar I would have been running pipelines I couldn't explain and hoping they worked, which is the opposite of what I wanted this project to be.

When you put all of that together, radar just had no version that worked for me. It was hardware, plus human data collection, plus heavy signal processing, all before the interesting part even started. Every direction hit a wall I couldn't get over on my own.

So I dropped it.

That felt worse than it sounds. I'd put real time into the idea and gotten attached to it, and letting it go was not fun. But looking back, cutting a bad idea early is one of the more useful things I've done so far. The proposal wasn't wasted, because the thinking carried over. I'd started asking better questions, like "where does the data actually come from" and "what's the smallest version of this I can do well." Both of those pointed straight at pressure mats.

So what is a pressure mat? It's a grid of force sensors you lie on. When you sleep on it, your body leaves a pressure map, heavier where your hips and shoulders push down and lighter everywhere else. From that map you can tell posture apart: on your back, on your left side, on your right side.

Everything that made radar impossible went the other way here. Public datasets already exist, so I can start today on real data without collecting anything myself. It's all software, so there's no board to buy, nobody to recruit, no lab. And a pressure map is just a small grid of numbers, so I can follow the whole thing from start to finish and actually explain it.

It also gave me a sharper question. Instead of "can radar do everything," I get one clean and useful one: how much sensor resolution does sleep-posture sensing actually need? Can a cheap, low-resolution mat do as well as an expensive high-resolution one?

That question is the whole project now. And I think it's a better project than radar ever would have been, partly because I was willing to kill the first idea.

More on that question, and the answer that surprised me, in the next post.

---

*A quick note on the date: like the other early posts, this one is dated to when it actually happened, back near the start of the project, even though I'm writing it up later. I explain why in the [welcome post](/blog/welcome-and-why-im-writing-this/).*
