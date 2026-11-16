---
title: "Was it just overfitting?"
date: 2026-08-13
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

The two explanations for the upside-down U needed different fixes. If the ResNet and the small CNN were overfitting, better training should rescue them at full resolution. If the full-resolution data itself contained something harmful, better training wouldn't help, and only averaging sensors would. So the experiment was easy to describe: train the same models again with settings that fight overfitting, and see whether the full-resolution scores come back up.

I added three changes at once. Gradient clipping puts a cap on how big a single update to the model can be, so one bad batch can't push it far off. Label smoothing stops the model from aiming for 100 percent confidence on the training answers, which goes straight at the overconfidence I had measured. Warmup starts training with a small learning rate for the first 3 epochs and then raises it. I ran this on the four neural networks, at all six resolutions, with the same 13 rounds and 3 seeds as before. That made 936 runs, saved in a separate CSV so they could never get mixed up with the first experiment.

The two models gave two different answers.

The ResNet came back. At full resolution it went from 0.803 to 0.967, almost as high as its best score of 0.980 at 10 by 21. So for the ResNet, the problem had mostly been training. A model with 313,000 parameters and only 11 people to learn from needed to be held back more than my default settings did.

The small CNN didn't. It went from 0.867 to 0.873, which is basically no change. With all three settings, something was still costing it about ten points at full resolution, something that averaging could fix and better training couldn't. That points to the second explanation, that the full-resolution picture carries detail that has nothing to do with posture and actually gets in the way. I started calling this the information effect. The readings at the 4,095 ceiling were still on my list as one possible part of it.

The other two networks hardly changed, plus 0.013 for the Transformer model and plus 0.016 for PointNet. That was what I hoped to see, because they never had the upside-down U in the first place. If the new settings had suddenly raised every model, I would have had to suspect the settings themselves.

My first reaction to the mixed result was disappointment. I wanted one clean explanation, and instead each model had its own. After thinking about it for a day, I changed my mind. The mixed answer says the upside-down U is two separate things that happen to look the same on a graph. If I had only tested one of the two models, I would have told half of the story and believed it was all of it.

There are two weaknesses I know about. First, I changed three settings together, so I can't say which one did the work. My guess is label smoothing, because the main symptom was overconfidence and that is exactly what it targets, but it stays a guess until I test each setting by itself. Second, someone could ask whether the first experiment was just badly tuned. In a way it was, on purpose. It used the same plain settings for every model and every resolution, so that resolution was the only thing changing. This experiment is the one that asks what happens with better training, and the difference between the two is the result.

Everything so far had been about using fewer sensors. The other way of making a mat worse, a smaller mat that covers less of the body, was next.
