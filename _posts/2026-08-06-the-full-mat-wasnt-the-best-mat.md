---
title: "The full mat wasn't the best mat"
date: 2026-08-06
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

The rerun finished without a single failure. All 1,638 runs were in the CSV this time, and I checked the row count twice before I let myself look at anything else.

Going in, I expected a simple picture. With fewer sensors the models would get worse, and somewhere along the way there would be a point where they fell apart. Finding that point for each posture was the whole goal of the experiment. The six resolutions went from the full 32 by 64 mat, which is 2,048 sensors, down to 4 by 8, which is 32. To make each smaller version I averaged neighboring sensors together, so the mat keeps its size and just has fewer, bigger sensors.

The first thing I noticed was that there was no point where things fell apart. The random forest scored 0.974 macro-F1 at full resolution. At 32 sensors, 64 times fewer, the best models were still above 0.92. The random forest and XGBoost barely moved across all six levels, and PointNet and the Transformer model looked about the same. I had been ready to write something like "side postures need at least this many sensors," and the data didn't have a line like that in it at all.

The second thing was stranger. Two models did worst at full resolution. The ResNet scored 0.803 with all 2,048 sensors, second to last of the seven. At a third of the resolution in each direction, 10 by 21, it scored 0.980, the highest number in the whole experiment. The small CNN did the same thing on a smaller scale, from 0.867 at full resolution to 0.976 at 10 by 21. Plotted against resolution, both of them went up and then came back down, like an upside-down U.

I had seen a hint of this before. When I looked at the partial results of the first run, at around 576 finished runs, the same two models were already doing worst at full resolution. I couldn't tell then whether it was real or just noise from an unfinished experiment. Now it was the complete experiment, with all 13 people and 3 seeds each, and it was still there.

It also made the ResNet hard to describe. Its score at full resolution was second to last. Its average over all six resolutions was in the middle. Its best single resolution was first. For a while I thought one of those numbers had to be wrong. Then I realized they were describing the same thing from different sides: a model that was being hurt by having too much input.

I could think of two explanations. The first is overfitting. At full resolution every frame is 2,048 numbers, but each training round only has 11 people. A ResNet with 313,000 parameters has plenty of room to memorize how those 11 people lie instead of learning what a posture looks like, and averaging sensors gives it less to memorize. The second explanation goes back to the readings that reach 4,095, the top of the 12-bit range. If some sensors were hitting that ceiling, the full-resolution picture would have flat spots that don't mean anything, and averaging could smooth them out. These are different kinds of problems. The first one is about the model and could be fixed with better training. The second one is about the data, and better training wouldn't touch it.

The linear SVM was the weakest model overall, 0.788 at full resolution, and it also did better with fewer sensors, peaking at 0.899 at 8 by 16. I didn't know yet what to make of that.

I wasn't ready to pick an explanation. First I wanted to make sure the upside-down U wasn't a coincidence, and then I needed an experiment that could tell the two explanations apart.
