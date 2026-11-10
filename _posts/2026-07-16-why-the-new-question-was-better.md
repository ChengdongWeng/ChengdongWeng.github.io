---
title: "Why the new question was better"
date: 2026-07-15
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

I went into that meeting last week ready to talk about radar. Partway through, my mentor started describing a completely different project, and I didn't see it coming at all.

I had ten prepared answers, and none of them were for this. For a few minutes I mostly nodded and wrote things down without really taking them in. I'd spent two weeks on the radar plan. I had the proposal, the outline, the timeline, the four rules, the list of questions. And now we were talking about pressure mats.

After the call I was pretty crushed. It felt like two weeks of work had just gone in the trash. I also had a worry I'm not proud of. Radar sounds cool. A grid of pressure numbers doesn't. I wasn't sure a pure software project on other people's data would even look like real research.

It took me a few days to start seeing it differently. What changed my mind wasn't anything big. It was how concrete the new plan was.

My mentor didn't just say "try pressure mats." He gave me actual steps. Find a public dataset recorded on a high-resolution mat. Train a model at full resolution as the baseline. Then make the mat worse on purpose, in software, retrain each time, and see where it starts to fail. There are two ways to make it worse. One is to shrink the mat so it covers less of the body. The other is to keep the size the same but space the sensors further apart, so each one stands for a bigger patch. The final answer should be a minimum resolution for each posture: how many sensors it takes to tell someone is on their back, and how many for their side.

I wrote both ways down as two separate steps on my list.

When I compared it with the radar plan, the difference was obvious. Radar had a question, but the steps to answer it were fuzzy: figure out how to collect data, build a model, hope the cheap board is good enough. This one had a question and a method, and I could start on every step of it right away. That's what made it feel doable instead of just ambitious.

It's also a real problem. Hospitals already use pressure mats to help prevent pressure sores, and they show up in some sleep trackers too. Good mats have thousands of sensors and cost a lot. If a mat with only a few dozen sensors could tell how someone is lying, that's a cheap product somebody could actually build. And I liked that either answer would be useful. If low resolution works, a cheap mat is enough. If it breaks at some point, then everyone knows where the line is.

The other thing I did was figure out how to keep this from turning into a small project. I split it into three layers. Layer one is my mentor's plan, done carefully on one dataset, and that part has to get done no matter what. Layer two is repeating it on more datasets, to make sure the answer isn't just a quirk of one mat. Layer three is optional: testing on a real cheap mat, if there's ever a good reason to buy one.

My radar idea came back in layer three. Training on one device and testing on another is exactly what I'd been excited about two weeks before, just with a different sensor. Seeing that made me feel a lot better.

Writing it down in layers helped more than I expected. Layer one meant that if I did the work, there would be a result. The other two meant the project still had room to grow. By now I've stopped thinking of it as a shrunken version of the old project.

Next, I had to set everything up from zero.
